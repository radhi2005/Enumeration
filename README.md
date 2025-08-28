# Explore Google hacking and enumeration 

# AIM:

To use Google for gathering information and perform enumeration of targets

## STEPS:
# NAME:RADHIMEENA M 
# REG NO:212223040159

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various Google hacking keywords and enumeration tools as follows:


### Step 3:
Open terminal and try execute some kali linux commands

## Pen Test Tools Categories:  

| Operator    | Description                        | Example Usage           |
| ----------- | ---------------------------------- | ----------------------- |
| `site:`     | Search within a specific domain    | `site:example.com`      |
| `inurl:`    | Search in URL                      | `inurl:admin`           |
| `intitle:`  | Search in page title               | `intitle:"index of"`    |
| `filetype:` | Search by file type                | `filetype:pdf`          |
| `intext:`   | Search inside page text            | `intext:"confidential"` |
| `link:`     | Pages that link to a specific site | `link:example.com`      |
| `cache:`    | View cached version of a site      | `cache:example.com`     |
| `ext:`      | Same as filetype                   | `ext:xls`               |

 ## Architecture 
 ```
+----------------------+
|   Attacker / Hacker  |
|   (Browser & Google) |
+----------+-----------+
           |
           | Google Dork Queries
           v
+---------------------------+
|       Google Search       |
+---------------------------+
           |
           | Indexed Public Content
           v
+---------------------------+
|   Target Websites / Data  |
| - Leaked files            |
| - Open directories        |
| - Sensitive info          |
+---------------------------+

```

# Output:
## SITE

![WhatsApp Image 2025-08-25 at 08 39 17_f144b8d6](https://github.com/user-attachments/assets/63e73917-f47c-40e4-8d84-6a4671fe4bd1)

## INTEXT
![WhatsApp Image 2025-08-25 at 08 41 51_7f98232a](https://github.com/user-attachments/assets/3600b904-2116-490e-8c3b-3c6ff0f2ebb6)

## FILETYPE
![WhatsApp Image 2025-08-25 at 08 40 32_52402f1e](https://github.com/user-attachments/assets/7eeb3e3c-af2a-492d-b3c8-bc88b2e394f2)

## INURL
<img width="1919" height="950" alt="image" src="https://github.com/user-attachments/assets/2feba6fa-611f-4d09-8f0b-ec52e72e98ce" />

## inurl:index ofm
<img width="1890" height="952" alt="image" src="https://github.com/user-attachments/assets/f0f955fc-49b4-412a-8655-655e2f147dfa" />

## link:example.com
<img width="1913" height="948" alt="image" src="https://github.com/user-attachments/assets/1ad35691-c962-4e20-a16d-d7bcb1ca440b" />

## cache:flipkart.com
<img width="1451" height="940" alt="image" src="https://github.com/user-attachments/assets/c6bc74aa-26ab-4798-9930-1034237394e4" />


# DNS Enumeration


<img width="1218" height="684" alt="image" src="https://github.com/user-attachments/assets/595e0b6c-01d8-4ea4-9555-5bd478bc0dec" />


## DNS Recon

| Record Type | Meaning                        | Example Output                   |
| ----------- | ------------------------------ | -------------------------------- |
| A           | Host to IPv4 address           | `example.com -> 93.184.216.34`   |
| AAAA        | Host to IPv6 address           | `example.com -> ::1`             |
| MX          | Mail server info               | `mail.example.com`               |
| NS          | Name servers                   | `ns1.example.com`                |
| TXT         | Misc data (SPF, verifications) | `v=spf1 include:_spf.google.com` |
| CNAME       | Canonical names (aliases)      | `www -> example.com`             |

## Common Tools Used (Kali Linux)

| Tool           | Description                                | Usage Example                           |
| -------------- | ------------------------------------------ | --------------------------------------- |
| `nslookup`     | DNS lookup tool (simple queries)           | `nslookup example.com`                  |
| `dig`          | DNS lookup utility (detailed)              | `dig example.com any`                   |
| `host`         | Simple DNS querying tool                   | `host example.com`                      |
| `dnsenum`      | Perl script to enumerate DNS info          | `dnsenum example.com`                   |
| `fierce`       | DNS scanner to locate non-contiguous IPs   | `fierce -dns example.com`               |
| `dnsrecon`     | Powerful DNS enumeration script            | `dnsrecon -d example.com -a`            |
| `theHarvester` | Subdomain enumeration using search engines | `theHarvester -d example.com -b google` |


## OUTPUT:

### NSLOOKUP:
<img width="928" height="857" alt="image" src="https://github.com/user-attachments/assets/ec07a6c4-f721-4384-93fe-eb07014e898d" />

### DIG:
<img width="796" height="631" alt="image" src="https://github.com/user-attachments/assets/6cb30cf2-4716-4eb9-b605-fe3f7540a1f3" />

### HOST:
<img width="765" height="636" alt="image" src="https://github.com/user-attachments/assets/25893560-1825-4bc0-8ec8-eac9d2bce5c6" />

### DNSENUM:
<img width="1218" height="684" alt="image" src="https://github.com/user-attachments/assets/595e0b6c-01d8-4ea4-9555-5bd478bc0dec" />


### FIERCE:
<img width="698" height="603" alt="image" src="https://github.com/user-attachments/assets/4048f80b-b6c9-48b8-84a1-4506f64f7c4e" />

### theHarvester:
<img width="835" height="645" alt="image" src="https://github.com/user-attachments/assets/b83263e2-7724-484b-b786-c2a42ff63c60" />

## Architecture Diagram 
```
+-------------------+        +------------------+       +------------------+
|                   |        |                  |       |                  |
|   Attacker (You)  +------->|   Target Server   +<----->+    DNS Server    |
| Kali Linux / Parrot|       | (Mail / DNS Host) |       |  (Authoritative) |
+---------+---------+        +---------+--------+       +---------+--------+
          |                            ^                          ^
          |                            |                          |
          |                            |                          |
          |           +-----------------------------+            |
          |           |      Information Tools      |            |
          |           |-----------------------------|            |
          |           | smtp-user-enum              |            |
          |           | nmap --script smtp-enum-*   |            |
          |           | dnsenum                     |<-----------+
          |           +-----------------------------+
          |
          v
+-----------------------------+
|   Output/Report             |
|  - Usernames Found          |
|  - MX Records / Zones       |
|  - Subdomains / IPs         |
+-----------------------------+

```

## dnsenum
**Purpose:** A multithreaded Perl script to enumerate information from DNS servers.

**Use case:** Performs DNS zone transfers, brute force subdomains, and gather host IPs.

```
dnsenum example.com
```

## Output:
<img width="1218" height="684" alt="image" src="https://github.com/user-attachments/assets/595e0b6c-01d8-4ea4-9555-5bd478bc0dec" />



## smtp-user-enum
**Purpose:** Standalone tool used to enumerate valid users by using the VRFY, EXPN, or RCPT TO commands.

**Use case:** Brute-forces SMTP to find users.

```
smtp-user-enum -M VRFY -U users.txt -t <target-ip>
```
  
 ## Output
  <img width="920" height="385" alt="image" src="https://github.com/user-attachments/assets/fd8013e8-c6d0-44e6-84a9-5e101b09826c" />



## nmap –script smtp-enum-users.nse <hostname>

**Purpose:** Uses smtp-enum-users NSE script to enumerate valid users on an SMTP server.

**Use case:** Helps identify email accounts on mail servers.

```
nmap -p 25 --script smtp-enum-users.nse <target-ip>
```
## OUTPUT:
<img width="932" height="205" alt="image" src="https://github.com/user-attachments/assets/57626337-5202-4fb0-9802-248fd950024f" />



## RESULT:
The Google hacking keywords and enumeration tools were identified and executed successfully

