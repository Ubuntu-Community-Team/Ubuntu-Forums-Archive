---
title: "OpenManage on Feisty Server Problems"
date: 2007-06-14
forum: Dell  Ubuntu Support
---

### Post by neemers on 2007-06-14
Hi all!

I have a Dell PowerEdge 2650 that I just loaded Ubuntu Feisty Server edition on.  I am trying to get Dell OpenManage installed on it so I can monitor the hardware using Zenoss.  I really just want to monitor the temp and get alerts about hard drives falling out of the raid.  I was able to install OpenManage with the debian repository...

deb [ftp://ftp.sara.nl/pub/sara-omsa](ftp://ftp.sara.nl/pub/sara-omsa) dell sara

It installed but got an error at the end when it was trying to install some things.  The things it was trying to install was these I think....

apt-get install openipmi

and 

apt-get install ipmitool

This is the error I get.....

Reading package lists... Done
Building dependency tree
Reading state information... Done
ipmitool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dellomsa (5.2.0-2) ...
Checking that /etc/ld.so.conf contains required paths...
ln: creating symbolic link `/etc/delloma.d/srvadmin' to `/opt/dell/srvadmin': File exists
ln: creating symbolic link `/usr/sbin/omconfig' to `/opt/dell/srvadmin/oma/bin/omconfig': File exists
ln: creating symbolic link `/usr/sbin/omexec' to `/opt/dell/srvadmin/oma/bin/omexec': File exists
ln: creating symbolic link `/usr/sbin/omhelp' to `/opt/dell/srvadmin/oma/bin/omhelp': File exists
ln: creating symbolic link `/usr/sbin/omreport' to `/opt/dell/srvadmin/oma/bin/omreport': File exists
ln: creating symbolic link `/usr/sbin/omupdate' to `/opt/dell/srvadmin/oma/bin/omupdate': File exists
Loading kernel modules
[: 212: ia64: unexpected operator
[: 212: x86_64: unexpected operator
/etc/init.d/instsvcdrv: 2551: arith: syntax error: "SECS + 1"
Starting dataengine
[: 212: ia64: unexpected operator
[: 212: x86_64: unexpected operator
/etc/init.d/instsvcdrv: 2551: arith: syntax error: "SECS + 1"
[: 212: ia64: unexpected operator
[: 212: x86_64: unexpected operator
/etc/init.d/instsvcdrv: 2551: arith: syntax error: "SECS + 1"
dpkg: error processing dellomsa (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 dellomsa
E: Sub-process /usr/bin/dpkg returned an error code (1)


They both give the same errors.....

Anyone got this installed on Feisty?  Or can point me to some helpful info please?

Thank you all!

---

### Post by neptho on 2007-06-16
Looks like a broken shell script.

Run this:
```
%sudo dpkg-reconfigure dash
```

Then choose *NO*, to allow Bash to be used for /bin/sh.  I bet that'll fix it right up.  If not, there's a very broken script in their build and you may wish to alert them to that fact.

---

### Post by neemers on 2007-06-18
GREAT!!  That worked!  Thank you very much neptho!

Do you know  if SNMP is setup during the install of the linux OpenManage?  I'm trying to do an snmpwalk of the server and I'm not coming up with any OpenManage Mibs.  I do have snmpd installed and I'm monitoring the server, but doing an snmpwalk with a dell Mib will not show anything.  Like this command should show me some CPU temps...

snmpwalk -v1 -c 192.168.1.201 .1.3.6.1.4.1.674.10892.1.700.12.1.6.1.1

But it comes up with nothing, while Servers with Win 2003 and OpenManage installed will show me a temp.  Any ideas on this?

Thank you community!

---

### Post by neptho on 2007-06-19
I do not believe that any but the standard 'system' MIBs are available by default.  Have you looked at the numeric OIDs?

Try this to see if it even gives you the proper interfaces:

```
snmpwalk -Of -v2c -c public localhost interfaces
```

If that works, then it's a trick to just track down the right OID: [which you're not alone with trying to discern..](http://209.85.165.104/search?q=cache:wYPLe0BqxMIJ:lists.us.dell.com/pipermail/linux-poweredge/2006-September/027378.html+http://lists.us.dell.com/pipermail/linux-poweredge/2006-September/027378.html&hl=en&ct=clnk&cd=1&gl=cr)

---

### Post by neemers on 2007-06-19
Well I have had SNMP and SNMPD installed on this machine and have been monitoring it with Zenoss.  The thing is, when I snmpwalk a specific OID that should give me a read out, I get nothing.  I know the temp OIDs because I'm monitoring the same model servers which are running Win 2003 and have OpenManage installed.  I figure that when I installed OpenManage it would install all the MIBs and allow snmp......

This is what I get with the command you said to run...

/home/myserver# snmpwalk -Of -v2c -c public localhost interfaces
.iso.org.dod.internet.mgmt.mib-2.interfaces = No more variables left in this MIB View (It is past the end of the MIB tree)

I figure I would get an error since it's not the community i have set in SNMPD.conf, so I tried with my community...

root@mail:/home/myserver# snmpwalk -Of -v2c -c mycomunity localhost interfaces
Timeout: No Response from localhost

Any ideas?

Thank you all!

---

### Post by neemers on 2007-06-19
This is what my snmpd.conf file looks like...  I made a bunch of changes from read me's and setups I found from Dell and other sources on getting snmp for OMSA working...

###########################################################################
#
# snmpd.conf
#
#   - created by the snmpconf configuration program
#
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

#syslocation Unknown (configure /etc/snmp/snmpd.local.conf)

# syscontact: The contact information for the administrator
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysContact.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  contact_string

#syscontact Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)












###########################################################################
# SECTION: Access Control Setup
#
#   This section defines who is allowed to talk to your running
#   snmp agent.

# rocommunity: a SNMPv1/SNMPv2c read-only access community name
#   arguments:  community [default|hostname|network/bits] [oid]

rocommunity  mycommunity 192.168.1.12





#
# Unknown directives read in from other files by snmpconf
#
# com2sec paranoid  default         public
com2sec readwrite default mycommunity
group MyROSystem v1        paranoid
group MyROSystem v2c       readwrite
group MyROSystem usm       paranoid
group MyROGroup v1         readonly
group MyROGroup v2c        readwrite
group MyROGroup usm        readonly
group MyRWGroup v1         readwrite
group MyRWGroup v2c        readwrite
group MyRWGroup usm        readwrite
view all    included  .1                               80
view system included  .iso.org.dod.internet.mgmt.mib-2.system
access MyROSystem ""     any       noauth    exact  system none   none
access MyROGroup ""      any       noauth    exact  all    all   none
access MyRWGroup ""      any       noauth    exact  all    all    none
smuxpeer .1.3.6.1.4.1.674.10892.1
trapsink 192.168.1.12 mycommunity

---

### Post by apel_2804 on 2007-06-19
To see the Server in an application like IT Assistant from Dell your snmp.conf should look like this:

[http://www.tbaumi.de/blog/?p=5](http://www.tbaumi.de/blog/?p=5)

There is a copy of my smpd.conf which works fine on an PE830 with Server Administrator and IT Assistant. It's with CentOS but it also uses openipmi. It's easyer if you first install openipmi and then OMSA, cause OMSA will then edit the snmp.conf...

---

### Post by neemers on 2007-06-19
Okay well I tried multiple things and ended up just putting in your snmpd.conf info you posted right into mine and thats all that is in there now.  So when I do some snmpwalks of known OID's I get errors.... are the OID's the same in OpenManage for linux?

root@mail:/home/myuser# snmpwalk -Of -v2c -c mycommunity localhost .1.3.6.1.4.1.674.10892.1.700
.iso.org.dod.internet.private.enterprises.674.10892.1.700 = No Such Object available on this agent at this OID

root@mail:/home/myuser# snmpwalk -Of -v2c -c mycommunity localhost .1.3.6.1.4.1.674.10892.1.700.12.1.6.1.1
.iso.org.dod.internet.private.enterprises.674.10892.1.700.12.1.6.1.1 = No Such Object available on this agent at this OID

Thank you all so far for your help!

Edit:
If I add a word instead of an OID I get some results i guess.... I did CPU instead of an OID...

root@mail:/home/faucetadmin# snmpwalk -Of -v2c -c DeltaFaucet1019 localhost CPU
.iso.org.dod.internet.private.enterprises.ucdavis.systemStats.ssCpuRawSoftIRQ.0 = Counter32: 7

---

### Post by RaySeys on 2007-07-02
Try removing -I smux from the snmpdopts line in /etc/default/snmpd

then /etc/init.d/snmpd restart 

now try to do the snmpwalk 

That fixed the problems for me. I found the line Unknown Token: smuxpeer in /var/log/syslog which led me to this solution.

I also did /etc/init.d/dataeng snmpenable to enable snmp not sure if this is necessary or not

---

