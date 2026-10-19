# soc-tier1-phishing-url-investigation
Tier 1 SOC Analyst portfolio project investigating a suspicious URL using VirusTotal, URLScan.io, AbuseIPDB, PhishTank, and hash analysis. Documents threat intelligence findings, IOC analysis, risk assessment, and phishing investigation methodology.

Phishing URL Investigation Report
SOC Tier 1 Analyst Portfolio

Analyst: Chuma Dlela

Analysis Date: 19 October 2026

Case ID: SOC-URL-001

Investigation Type: Phishing URL Investigation

Status: Likely phishing

Target URL: https://allegro-lokalnie.zoomarea.sbs/

1. Executive Summary

The suspicious URL was investigated using URLScan.io, VirusTotal, AbuseIPDB, PhishTank, and a hash-identification tool. VirusTotal had a detection ratio of 7/93, with several security vendors identifying the URL as phishing, malware, spam, or suspicious. URLScan.io highlighted Cloudflare infrastructure, a page title different from the apparent brand, and multiple links to similar websites.

Based on the evidence, the URL is likely phishing. Credential theft, malware execution, and the URL’s true owner remain unproven.

2. Investigation Scope and Methodology


The investigation followed a Tier 1 SOC procedure:


1. Determine the suspicious URL and its hostname
2. Analyze the URL’s infrastructure using URLScan.io
3. Review the URL’s reputation and security vendors’ findings using VirusTotal
4. Determine the URL’s associated IP reputation using AbuseIPDB
5. Analyze the URL’s threat intelligence using PhishTank
6. Determine the hash values’ source and authenticity
7. Combine the evidence and formulate a conclusion
8. URL and Domain Analysis

3.Attribute FindingTarget URL https://allegro-lokalnie.zoomarea.sbs/
Hostname allegro-lokalnie.zoomarea.sbs
Registered domain zoomarea.sbs
Scheme HTTPS
Suspected brand Allegro Lokalnie
Observed infrastructure Cloudflare-associated
Initial assessment Suspicious
The hostname includes a brand string similar to Allegro Lokalnie but uses ZoomArea as the registered domain. A closer inspection is required since the URL uses a domain name different from the brand.

4. URLScan.io Analysis
Report: https://urlscan.io/result/01a152a1-246b-7058-b29e-3878e0f7b9d2/#transactions
Attribute Finding
Observed IP 172.67.137.5
Network provider Cloudflare, Inc.
Autonomous system AS13335
HTTP transactions 2
Domains contacted 1
IPs contacted 1
HTTPS requests 100%
Outgoing links 60
URLScan verdict No classification assigned
The URLScan.io report shows that the page’s title – Detailed Phone Report for (405) 609-5587: Photos & More – does not match the expected Allegro Lokalnie page. In addition, the report shows that the URL contains many links to similar websites, including allegrolokalnie.mysticcub.sbs, allegro.gorgetoss.sbs, olx.slickomega.sbs, and vinted.sofirst.cfd. This finding requires further inspection, but it does not confirm that all the links are malicious.
The observed IP address 172.67.137.5 is a Cloudflare server, and the infrastructure should be considered untrusted.

5. VirusTotal Analysis Report: https://www.virustotal.com/gui/url/b1337f46f91400d8e0de48fdfb50d08bb25dc7cd96b6d7639f04898f5fbb0c5c/detection
Since the URL was scanned recently, the detection ratio is 7/93, as shown in the table below.
Security vendor Classification
AlphaMountain.ai Phishing
G DATA Phishing
PhishTank Phishing
Webroot Phishing
Bitdefender Phishing
Kaspersky Phishing
VIPRE Malware
Fortinet Spam
LevelBlue Suspicious
As seen from the table, most security vendors classified the URL as phishing, but the classifications were not consistent. On the other hand, the detection ratio is not sufficient to confirm that the URL is dangerous, and the ratio could have changed as of the analysis date.

6. AbuseIPDB Analysis
Report: https://www.abuseipdb.com/check/104.21.46.89
Attribute Finding
IP address 104.21.46.89
Network 104.16.0.0/13
Provider Cloudflare, Inc.
ASN AS13335
Report count 2
Current abuse confidence score 0%
The AbuseIPDB report confirms that the URL is hosted on Cloudflare servers. Since the abuse confidence is 0%, there is no sufficient evidence that the URL is a source of malicious traffic.
The analysis findings are consistent with the URLScan.io findings, and neither report provides enough evidence to confirm the URL’s malicious nature.

7. Hash Analysis
Hash A — Original supplied value
7d2870e0b9ded189d7107ec740ee4c8a7d2e8261a468ef644f1c58c2e6730f09
Length: 64 hexadecimal characters
Possible algorithm: SHA-256
Original input and connection to target URL: unverified

    Hash B — Value recorded from Hash Identifier
2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
The hash value represents the SHA-256 digest of the text hello . The two hash values are different, but Hash Identifier typically does not convert one hash into another. Therefore, an explanation is needed for Hash B’s origin and connection to the target URL.
Since the hash values are different, it is uncertain what the original input was for Hash B. In addition, both hashes are unconfirmed because there is no information on what process created them or where they came from.

8. Consolidated Indicators of Compromise
Indicator Type Assessment

https://allegro-lokalnie.zoomarea.sbs/ URL Likely phishing

allegro-lokalnie.zoomarea.sbs Hostname Suspected brand impersonation

zoomarea.sbs Registered domain Further investigation needed

104.21.46.89 IPv4 Cloudflare-associated infrastructure

172.67.137.5 IPv4 Cloudflare-associated infrastructure

Hash A Hash Algorithm and provenance unverified

Hash B Hash SHA-256 of hello ; association with target unverified

9. Final Verdict

Classification: Likely phishing

Confidence: Medium 

Potential severity: High if page contains credentials or sensitive information

Reasoning

The URL contains a hostname with a brand name different from the registered domain. In addition, VirusTotal detected several phishing vendors, and the URLScan.io report showed that the URL’s page title did not match the expected brand and had multiple links to similar websites. The AbuseIPDB report did not confirm that the URL is a source of malicious traffic, although the URL is hosted on Cloudflare servers.
Based on the evidence, it is possible that the URL is phishing since it uses brand impersonation and has multiple blacklisted links. However, further investigation is required to confirm whether the URL attempted to steal credentials, execute malware, or reveal the website’s true owner.


10. Recommended Actions
Preserve the URL, screenshots, and scan records
Submit the URL to the organization’s approved threat intelligence workflow
Block the URL or hostname if appropriate
Inspect the DNS, proxy, firewall, or endpoint logs if users accessed the URL
Determine if the URL prompted for or stole any credentials or sensitive information
If the URL prompted for or stole credentials, reset the password in the legitimate service and revoke the compromised session
If the URL caused a file to be downloaded, apply the organization’s controlled malware analysis procedure
Avoid blocking all Cloudflare infrastructure based on this incident
Record the evidence, including timestamps and report links, for audit and repeat investigation


11. Evidence and References

URLScan.io report
VirusTotal URL analysis
AbuseIPDB IP report
PhishTank

12. Skills Demonstrated

 Suspicious URL triage

 Threat intelligence enrichment

 Domain and hostname analysis

 Security vendor result correlation

 IP reputation analysis
 
 Cloudflare reverse-proxy interpretation

 Hash format identification

 IOC documentation

 Evidence preservation

 Risk assessment and escalation

13. Conclusion

   The investigation illustrates a Tier 1 analyst’s approach to analyzing a suspicious URL using multiple pieces of evidence. In this case, the strongest proof was the VirusTotal findings, which showed that        several security vendors detected the URL as phishing. Another significant discovery was the URLScan.io report, which found that the URL’s page title did not match the claimed brand and that the URL had many    similar and potentially malicious links.

  The investigation also shows the limitations of some security tools, including hash identifiers and reputation services. For example, Cloudflare infrastructure could not be used to determine the true URL                owner, and hash values did not help confirm whether the URL was malicious. These weaknesses were considered in the final assessment. Based on the evidence, the analyst concludes that the URL is likely phishing and recommends preserving the evidence for further analysis.

Final assessment: Likely phishing – preserve evidence and escalate for further investigation.
