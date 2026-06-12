---
title: "Having some issues getting Snort to run"
date: 2008-12-23
forum: General Help
---

### Post by djbeenie on 2008-12-23
42 client (Footprint)
      53 client (Footprint)
      80 client (Footprint)
      110 client (Footprint)
      111 client (Footprint)
      135 client (Footprint)
      136 client (Footprint)
      137 client (Footprint)
      139 client (Footprint)
      143 client (Footprint)
      445 client (Footprint)
      513 client (Footprint)
      1433 client (Footprint)
      1521 client (Footprint)
      3306 client (Footprint)
    Bound Addresses:0.0.0.0/0.0.0.0
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /etc/snort/unicode.map
      IIS Unicode Map Codepage: 1252
    DEFAULT SERVER CONFIG:
      Server profile: All
      Ports: 80 8080 8180
      Flow Depth: 300
      Max Chunk Length: 500000
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
      Ascii: YES alert: NO
      Double Decoding: YES alert: YES
      %U Encoding: YES alert: YES
      Bare Byte: YES alert: YES
      Base36: OFF
      UTF 8: OFF
      IIS Unicode: YES alert: YES
      Multiple Slash: YES alert: NO
      IIS Backslash: YES alert: NO
      Directory Traversal: YES alert: NO
      Web Root Traversal: YES alert: YES
      Apache WhiteSpace: YES alert: NO
      IIS Delimiter: YES alert: NO
      IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG
      Non-RFC Compliant Characters: NONE
      Whitespace Characters: 0x09 0x0b 0x0c 0x0d
rpc_decode arguments:
    Ports to decode RPC on: 111 32771
    alert_fragments: INACTIVE
    alert_large_fragments: ACTIVE
    alert_incomplete: ACTIVE
    alert_multiple_requests: ACTIVE
Portscan Detection Config:
    Detect Protocols:  TCP UDP ICMP IP
    Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan
    Sensitivity Level: Low
    Memcap (in bytes): 10000000
    Number of Nodes:   36900

Tagged Packet Limit: 256

+-----------------------[thresholding-config]----------------------------------
| memory-cap : 1048576 bytes
+-----------------------[thresholding-global]----------------------------------
| none
+-----------------------[thresholding-local]-----------------------------------
| none
+-----------------------[suppression]------------------------------------------
| none
-------------------------------------------------------------------------------
Rule application order: activation->dynamic->pass->drop->alert->log
Log directory = /var/log/snort
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/..                             .
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf                             _ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf                             _ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf                             _dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf                             _smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf                             _dns_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicprep                             rocessor/
FTPTelnet Config:
    GLOBAL CONFIG
      Inspection Type: stateful
      Check for Encrypted Traffic: YES alert: YES
      Continue to check encrypted data: NO
    TELNET CONFIG:
      Ports: 23
      Are You There Threshold: 200
      Normalize: YES
      Detect Anomalies: NO
    FTP CONFIG:
      FTP Server: default
        Ports: 21
        Check for Telnet Cmds: YES alert: YES
        Identify open data channels: YES
      FTP Client: default
        Check for Bounce Attacks: YES alert: YES
        Check for Telnet Cmds: YES alert: YES
        Max Response Length: 256
SMTP Config:
      Ports: 25
      Inspection Type:            STATEFUL
      Normalize Spaces:           YES
      Ignore Data:                NO
      Ignore TLS Data:            NO
      Ignore Alerts:              NO
      Max Command Length:         0
      Max Header Line Length:     0
      Max Response Line Length:   0
      X-Link2State Alert:         YES
      Drop on X-Link2State Alert: NO

DCE/RPC Decoder config:
    Autodetect ports ENABLED
    SMB fragmentation ENABLED
    DCE/RPC fragmentation ENABLED
    Max Frag Size: 3000 bytes
    Memcap: 100000 KB
    Alert if memcap exceeded DISABLED

DNS config:
    DNS Client rdata txt Overflow Alert: ACTIVE
    Obsolete DNS RR Types Alert: INACTIVE
    Experimental DNS RR Types Alert: INACTIVE
    Ports: 53

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
7907 Snort rules read
    7907 detection rules
    0 decoder rules
    0 preprocessor rules
7907 Option Chains linked into 490 Chain Headers
0 Dynamic rules
+++++++++++++++++++++++++++++++++++++++++++++++++++

Verifying Preprocessor Configurations!
Warning: flowbits key 'dce.bind.nddeapi' is set but not ever checked.
Warning: flowbits key 'ms_sql_seen_dns' is checked but not ever set.
Warning: flowbits key 'smb.tree.bind.nddeapi' is checked but not ever set.
Warning: flowbits key 'community_uri.size.1050' is set but not ever checked.
297 out of 512 flowbits in use.
***
*** interface device lookup found: eth0
***

Initializing Network Interface eth0
Decoding Ethernet on interface eth0
database: compiled support for ( mysql )
database: configured to use mysql
database:          user = snort
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = 10.1.10.2
database:     sensor id = 1
database: schema version = 107
database: using the "alert" facility
database: compiled support for ( mysql )
database: configured to use mysql
database: must enter database name in configuration file


USAGE: database plugin

 output database: [log | alert], [type of database], [parameter list]

 [log | alert] selects whether the plugin will use the alert or
 log facility.

 For the first argument, you must supply the type of database.
 The possible values are mysql, postgresql, odbc, oracle and
 mssql
 The parameter list consists of key value pairs. The proper
 format is a list of key=value pairs each separated a space.

 The only parameter that is absolutely necessary is "dbname".
 All other parameters are optional but may be necessary
 depending on how you have configured your RDBMS.

 dbname - the name of the database you are connecting to

 host - the host the RDBMS is on

 port - the port number the RDBMS is listening on

 user - connect to the database as this user

 password - the password for given user

 sensor_name - specify your own name for this snort sensor. If you
        do not specify a name one will be generated automatically

 encoding - specify a data encoding type (hex, base64, or ascii)

 detail - specify a detail level (full or fast)

 ignore_bpf - specify if you want to ignore the BPF part for a sensor

              definition (yes or no, no is default)

 FOR EXAMPLE:
 The configuration I am currently using is MySQL with the database
 name of "snort". The user "snortusr@localhost" has INSERT and SELECT
 privileges on the "snort" database and does not require a password.
 The following line enables snort to log to this database.

 output database: log, mysql, dbname=snort user=snortusr host=localhost

ERROR: Fatal Error, Quitting..


This is my Output on my configuration..

  output database: alert, mysql, user=snort password=MYPASSWORD dbname=snort host=localhost

---

