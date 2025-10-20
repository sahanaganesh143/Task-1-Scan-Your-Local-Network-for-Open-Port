#Scan-Your-Local-Network-for-Open-Port
Task-1 involves scanning for open ports, identifying which ports are open or closed and scanning for vulnerabilities. 

To find local ip address use Windows Command Prompt and type:


>ipconfig


(output will be shown similar to "ipconfig." image attatched.)

The IPV4 address and Subnet Mask address are the required values to inspect ports. Convert IPV4 address to CIDR using the code given in file ('convert-to-cidr').

TCP SYN scan: (enter your CIDR)

>nmap -sS 192.168.1.0/24 -oN nmap_synscan.txt


#enter your CIDR address, this output will be saved as a txt file

To check for open ports: (enter your CIDR)

>nmap -sS -sV 192.168.1.0/24 -oA nmap_fullscan

Specific useful scripts:
#To detect the SSH service/version (scan port-22)

>nmap -p22 --script ssh-hostkey,ssh2-enum-algos -sV 192.168.1.100 -oN ssh_info.txt

#Scans ports 80 and 443 (HTTP/HTTPS), does service/version detection

>nmap -p80,443 --script http-title,http-enum -sV 192.168.1.100 -oN http_info.txt

#NSE script to gather SMB/Windows info

>nmap -p139,445 --script smb-os-discovery -sV 192.168.1.100 -oN smb_info.txt

#NSE script to inspect RDP encryption settings

>nmap -p3389 --script rdp-enum-encryption -sV 192.168.1.100 -oN rdp_info.txt


General scan of Vulnerability: using vuln

>nmap -sS -sV --script vuln 192.168.1.100 -oN vuln_scan.txt





