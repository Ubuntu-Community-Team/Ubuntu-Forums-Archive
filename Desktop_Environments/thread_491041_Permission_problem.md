---
title: "Permission problem???"
date: 2007-07-03
forum: Desktop Environments
---

### Post by williemerwe on 2007-07-03
Hi, 

I've successfully installed cacti on Ubuntu. I can monitor traffic, graphs generate, etc. Problem is when I add a certain device which uses a not-cacti-standard .xml file. I can create the device and the SNMP seems to communicate between the two, but I get the following error when trying to attach the Data Query to the device: 
Warning: file(/var/www/cacti/resource/snmp_queries/allot-pipe.xml) [function.file]: failed to open stream: Permission denied in /var/www/cacti/lib/data_query.php on line 79 

Warning: implode() [function.implode]: Bad arguments. in /var/www/cacti/lib/data_query.php on line 79 

Warning: file(/var/www/cacti/resource/snmp_queries/allot-pipe.xml) [function.file]: failed to open stream: Permission denied in /var/www/cacti/lib/data_query.php on line 79 

Warning: implode() [function.implode]: Bad arguments. in /var/www/cacti/lib/data_query.php on line 79 

Warning: file(/var/www/cacti/resource/snmp_queries/allot-pipe.xml) [function.file]: failed to open stream: Permission denied in /var/www/cacti/lib/data_query.php on line 79 

Warning: implode() [function.implode]: Bad arguments. in /var/www/cacti/lib/data_query.php on line 79 

Warning: file(/var/www/cacti/resource/snmp_queries/allot-pipe.xml) [function.file]: failed to open stream: Permission denied in /var/www/cacti/lib/data_query.php on line 79 

Warning: implode() [function.implode]: Bad arguments. in /var/www/cacti/lib/data_query.php on line 79 

Warning: Cannot modify header information - headers already sent by (output started at /var/www/cacti/lib/data_query.php:79) in /var/www/cacti/host.php on line 72 

I have no idea what this means or how to rectify. I recon it's a permission problem somewhere, but where...??? 

/var/www/cacti/lib/data_query.php on line 79: 
$data = implode("",file($xml_file_path)); 

/var/www/cacti/host.php on line 72: 
header("Location: host.php?action=edit&id=" . $_GET[host_id]); 

When I open the device again, I get a "Success" prompt, but no info: 
Associated Data Queries 
Data Query Name Debugging Re-Index Method Status 
1) Allot Pipe-DQ (Verbose Query) Index Count Changed Success [0 Items, 0 Rows] 

Note: When I do the same on WINXP with cacti, I don't get this error. 

Any suggestions will be appreciated.

---

