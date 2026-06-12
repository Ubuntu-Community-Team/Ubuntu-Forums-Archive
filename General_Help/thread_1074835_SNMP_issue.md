---
title: "SNMP issue"
date: 2009-02-19
forum: General Help
---

### Post by wililupy on 2009-02-19
Hello,

I installed SNMP from the repository on my ubuntu server 8.04. I have it configured with the following /etc/snmp/snmpd.conf:


###########################################################################
#
# snmpd.conf
#
#   - created by the snmpconf configuration program
#
###########################################################################
# SECTION: Monitor Various Aspects of the Running Host
#
#   The following check up on various aspects of a host.

# disk: Check for disk space usage of a partition.
#   The agent can check the amount of available disk space, and make
#   sure it is above a set limit.
#
#    disk PATH [MIN=100000]
#
#    PATH:  mount path to the disk in question.
#    MIN:   Disks with space below this value will have the Mib's errorFlag set.
#           Can be a raw byte value or a percentage followed by the %
#           symbol.  Default value = 100000.
#
#   The results are reported in the dskTable section of the UCD-SNMP-MIB tree
disk  / 20%
disk  /var 25%

# load: Check for unreasonable load average values.
#   Watch the load average levels on the machine.
#
#    load [1MAX=12.0] [5MAX=12.0] [15MAX=12.0]
#
#    1MAX:   If the 1 minute load average is above this limit at query
#            time, the errorFlag will be set.
#    5MAX:   Similar, but for 5 min average.
#    15MAX:  Similar, but for 15 min average.
#
#   The results are reported in the laTable section of the UCD-SNMP-MIB tree

load  15 12 10






###########################################################################
# SECTION: System Information Setup
#
#   This section defines some of the information reported in
#   the "system" mib group in the mibII tree.

# syslocation: The [typically physical] location of the system.
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysLocation.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  location_string

syslocation  "Removed for privacy"

# syscontact: The contact information for the administrator
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysContact.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  contact_string

syscontact  "removed for privacy"



###########################################################################
# SECTION: Access Control Setup
#
#   This section defines who is allowed to talk to your running
#   snmp agent.
#   arguments:  community [default|hostname|network/bits] [oid]

rocommunity  public

# EOF

When I run snmpwalk -v1 -c public localhost

I get the standard response of it communicating with the server and getting the information. However, when I run snmpwalk -v1 -c public *hostname *

It gets Timeout: No Response from *hostname*

We use Intermapper to monitor our servers, and it can't communicate to this machine. I currently have it just using a ping status. When I first installed this server, it worked, but since then, we had to rebuild the server due to hardware failure, and now snmp is not working.

It seems like maybe a firewall issue, but unless Ubuntu Server 8.04 comes with a firewall or port 161 locked down from any outside connection except localhost, I don't see this as being the problem. 

Any ides?

Thanks, 
Luke

---

