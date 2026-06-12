---
title: "Connection to CVS no longer works after Jaunty upgrade"
date: 2009-05-03
forum: General Help
---

### Post by aaamos on 2009-05-03
Hi All,

I've had cvs and cvsd installed since Hardy or earlier, mainly following [these instructions]("http://bobbyallen.wordpress.com/2006/11/06/building-a-cvs-server-on-ubuntu-606-server/") quite some time ago. Ever since the upgrade to Jaunty, trying to connect gives me a "connect to [...] failed: Connection refused" error.

I've tried removing and re-installing cvs and cvsd, setting up the user again to make absolutely sure I've got the right password, and I've googled and searched the forums to no avail.

Anyone know how I can get my cvs server back to working in Jaunty? Thanks in advance.

Cheers,

Amos

P.S.: I noticed that on the re-install, it wouldn't let me edit the /var/lib/cvsd/cvsroot/CVSROOT/config file without changing owner and making it read-write, which I don't recall having to do the first time around.

---

### Post by mehdic on 2009-05-03
Same problem here.
When I do /etc/init.d/cvsd start there are no errors but the cvsd daemon never starts.
Any help appreciated...

---

### Post by mehdic on 2009-05-04
Ok problem is SOLVED. 
I had to change the "Listen" configuration in  /etc/cvsd/cvsd.conf
from 
Listen * 2401
Listen 192.168.1.XXX 2401

where 192.168.1.XXX is my local static IP.
then restart cvsd
/etc/init.d/cvsd restart

Hope this helps

---

### Post by aaamos on 2009-05-05
Thanks mehdic, that helped - I still have permission problems though, trying to either commit or checkout. CVS tries to create a #cvs.lock file but gets a permission denied... I've tried removing and re-installing cvsd, but it hasn't helped.

---

### Post by mehdic on 2009-05-08
Login as root and delete the cvs.pid or cvs.lock file

then try 
sudo /etc/init.d/cvsd start

Should be able to have it running

---

### Post by aaamos on 2009-05-13
I still have those permission problems - I can browse the repository, but for example adding files, I get "cvs add: cannot mkdir /cvsroot/filename: Permission denied", checking out, I get:

The server reported an error while performing the "cvs status" command.
  [projectname]: cvs status: failed to create lock directory for `/cvsroot/[projectname]' (/cvsroot/[projectname]/#cvs.lock): Permission denied
  [projectname]: cvs status: failed to obtain dir lock in repository `/cvsroot/[projectname]'
  [projectname]: cvs [status aborted]: read lock failed - giving up

---

### Post by manfer on 2009-05-26
I'm not an expert on this, so It would be nice if someone with the knowledge can confirm this.

From my tests for some reason the server is not starting with the default configuration: Listen * 2401

If you have nmap installed on your system you can find what network services are running and in which port.

nmap 127.0.0.1

If cvspserver is not present on the list provided by that command then the server is not listening.

If you change Listen from * to local IP (192.168.2.XXX as someone says or 127.0.0.1 that would be the same as well) what you are doing, I think, is changing the ability of CVS Server to listen to any request except those that come from local IP. Does seems not a good replacement to * unless you only need local connection to CVS. If you need connections from other computers on local network or from other networks, those will be refused if you change * to local IP.

I found this on a FAQ and maybe this is the problem and a better solution.

> 
Why are tcp wrappers not working?

You currently have to enable tcp wrappers during configure time using the --with-libwrap option during configure. You can optionally specify the prefix for where the tcp wrapper libraries are located.

**Some versions of tcp wrappers have problems with hosts that support IPv6 connections. Try to get a patched version of tcp wrappers or replace the 'Listen * 2401' statement in cvsd.conf with 'Listen 0.0.0.0 2401'.**

Don't forget that the hosts.allow and hosts.deny need to be located inside the chroot jail to be effective.


So maybe 0.0.0.0 is a better replacement to * if you need connections from any computer. And if you need to allow or deny some host deal with those host.allow and hosts.deny that the FAQ says.

So what I would do is:

```

// Change the "Listen" configuration in /etc/cvsd/cvsd.conf

// From:
Listen * 2401

// To:
Listen 0.0.0.0 2401

// Then restart cvsd:
sudo /etc/init.d/cvsd restart

```

---

### Post by manfer on 2009-05-26
> **aaamos said:**
> I still have those permission problems - I can browse the repository, but for example adding files, I get "cvs add: cannot mkdir /cvsroot/filename: Permission denied", checking out, I get:

The server reported an error while performing the "cvs status" command.
  [projectname]: cvs status: failed to create lock directory for `/cvsroot/[projectname]' (/cvsroot/[projectname]/#cvs.lock): Permission denied
  [projectname]: cvs status: failed to obtain dir lock in repository `/cvsroot/[projectname]'
  [projectname]: cvs [status aborted]: read lock failed - giving up

I think this problem is related to permissions.

Again, I must say I'm not too familiar with CVS. I just needed one to make some test and I had same issues.

I'm going to make my example with /demo which is one of the repositories that the cvsd install script suggests by default. In many docs in web you can read when they explain how to create the repository:

```

sudo mkdir /var/lib/cvsd/demo
sudo chown -R cvsd:cvsd /var/lib/cvsd/demo
sudo cvs -d /var/lib/cvsd/demo init

```

That way, first command mkdir makes dir demo owned by root and with group root. Second command changes demo owner to cvsd and group to cvsd. Third command inits the repository (this generates a CVSROOT dir inside repository folder, in this case demo folder, and that folder and all its content is owned by root with group root).

But if you run those commands in other order (you can see this in some docs too, for example, the one you provide on first post):

```

sudo mkdir /var/lib/cvsd/demo
sudo cvs -d /var/lib/cvsd/demo init
sudo chown -R cvsd:cvsd /var/lib/cvsd/demo

```

Now first command creates demo folder, second inits demo repository, third makes demo folder and all its contents owned by cvsd and group cvsd.

I don't know if this is something wrong with cvs init that must generate all those files with proper user and group or just the correct way to run the commands is the second order and nothing more.

After that, use CVS as it is supposed to work to avoid those lock permission problems. For example don't move or copy manually a project to the repository with mv or cp commands. I think that is not the correct way to work with a CVS repository.

To add a project to repository you have to use the cvs client with import parameter. For example if I have a folder myproject in my home folder and I want to add it to CVS.

```

cd ~/myproject
cvs -d :pserver:cvsuser@localhost:/demo import -m "Initial commit" myproject FIRSTBRANCH initialversion

```

and that way the files are imported correctly to repository with proper owner and group, cvsd:cvsd.

---

### Post by blindrain on 2011-04-27
I still have this problem even after using the fix listed above


cvsd: debug: reading config file (/etc/cvsd/cvsd.conf)
cvsd: debug: done reading config file
cvsd: debug: cvscmd: /bin/cvs
cvsd: debug: cvsargs[0]: cvs
cvsd: debug: cvsargs[1]: -f
cvsd: debug: cvsargs[2]: --allow-root=/src
cvsd: debug: cvsargs[3]: pserver
cvsd: debug: cvsenv[0]: HOME=/
cvsd: debug: cvsenv[1]: PATH=/bin
cvsd: debug: cvsenv[2]: SHELL=/bin/sh
cvsd: debug: cvsenv[3]: TMPDIR=/tmp
cvsd: debug: cvsenv[4]: CVSUMASK=027
cvsd: version 1.0.18 starting
cvsd: debug: binding 0.0.0.0 443 family=2 socktype=1 protocol=6
cvsd: bind() failed: Address already in use
cvsd: version 1.0.18 bailing out


as you can see i've tried several different ports my particular issue i can telnet successfully into localhost and the local ip that starts 10. but i can't telnet from a remote machine this server is on an amazon server so everything should auto forward to the proper ports i thought maybe it was a firewall issue but nothing set to block in local iptables and i also bound it to known working ports turning other programs off that use them still nothing running ubuntu maverick

below is my config
# This is the configuration file for cvsd.
# See the manual page cvsd.conf(5) for more information.
#
# You can also use 'dpkg-reconfigure cvsd' to modify these
# settings.
#
# See the "Password authentication server"
# section in the cvs texinfo for more information
# about running a pserver.

# RootJail <path>
#  This is the location of the chroot jail
#  cvs should be run in.
#  Specify 'none' (without quotes) to not use
#  a chroot jail.
#  This directory should be initialized with
#  the cvsd-buildroot script.
RootJail /vol2/cvsowner/cvsd-root

# Uid <uid>
#  This specifies which user id cvs should be
#  run as. This can be a numerical id or
#  a symbolic value.
Uid entermedia

# Gid <gid>
#  This specifies which group id cvs should be
#  run as. This can be a numerical id or
#  a symbolic value.
Gid cvsd

# CvsCommand <path>
#  If you define this it should point to the cvs
#  command to execute. Otherwise "/bin/cvs" will
#  be used if a RootJail is configured and the
#  cvs command found at compiletime otherwise.
#  The path should be relative to the specified
#  RootJail and should start with a '/'.

# CvsArgs <arg>...
#  Additional arguments to pass to the cvs command.
#  For example, to enable read-only access to the
#  repository, pass the -R option.

# Nice <num>
#  This specifies the nice value (on most systems
#  ranging from -20 to 20) where the smaller the number
#  (more negative) the higher the priority.
Nice 1

# Umask <mask>
#  This specifies a umask used by the cvs pserver when
#  creating files. Specify as an octal value.
Umask 027

# Limit <resource> <value>
#  <resource> can be one of: coredumpsize, cputime, datasize, filesize,
#  memorylocked, openfiles, maxproc, memoryuse, stacksize or virtmem.
#  <value> is the maximum value for the given resource. For size values
#  a suffix of 'b', 'k' or 'm' can be specified ('k' is default). Time
#  values can be formatted as 'mm:ss' or have 'm' or 's' suffixes
#  ('s' is default).

# PidFile <file>
#  This specifies the location the process id of the
#  daemon is written.
PidFile /var/run/cvsd.pid

# Listen <address> <port>
#  The addresses and ports to listen on for connections.
#Listen * 2401
#Listen 0.0.0.0 2401
#Listen 10.255.146.210 2401

# MaxConnections <num>
#  The maximum number of connections that will
#  be handled simultaneously. 0 is unlimited.
MaxConnections 10

# Log <scheme/file> [<loglevel>]
#  The way logging is done. Either none, syslog or a
#  filename may be specified, followed by an optional
#  loglevel. Loglevel may be one of:
#  crit, error, warning, notice, info (default) or debug.
#  This option can be supplied multiple times.
#  If this option is not specified syslog info is assumed.
Log syslog info
#Log /var/log/cvsd.log debug

# Repos <path>
#  This option specifies which repositories
#  can be used. The value is passed as a
#  --allow-root=<path> parameter to cvs.
#  The path should be relative to the specified
#  RootJail and should start with a '/'.
#  This option can be supplied multiple times.

#Listen * 2401
#Listen 0.0.0.0 2401
Listen 0.0.0.0 443
#Listen 10.255.146.210 2401

#Repos /demo
#Repos /myrepos
Repos /src

---

