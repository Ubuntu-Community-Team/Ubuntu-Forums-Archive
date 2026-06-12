---
title: "apt-cacher problem"
date: 2009-05-28
forum: General Help
---

### Post by gforster on 2009-05-28
I have followed the debuntu guide on setting up apt-cacher so that I can easily update through our computer lab. The apt-cacher server is called "teacher" and I have update the sources.list on one of the clients for testing to reflect this. 

When i run the apt-get update command, I am told that it could not connect and it fails. Everything appears to be set correctly. What am i missing?

---

### Post by Skip Da Shu on 2009-05-29
> **gforster said:**
> I have followed the debuntu guide on setting up apt-cacher so that I can easily update through our computer lab. The apt-cacher server is called "teacher" and I have update the sources.list on one of the clients for testing to reflect this. 

When i run the apt-get update command, I am told that it could not connect and it fails. Everything appears to be set correctly. What am i missing?

What is missing is anything for anyone to give you any help!

Post at least your apt-cacher.conf file.

I'd also strongly recommend returning the client sources list to how it was (you did make a backup?).  Then instead of all that mess simple drop a 1 line file into /etc/apt/apt.conf.d/ called "01proxy".

In that file put 1 line:```
Acquire::http::Proxy "http://192.ipof.ur.aptcacher:3142";
```

See [**HERE**]("http://ubuntuforums.org/showpost.php?p=4841206&postcount=21") for more details.


PS: sorry 'bout the initial tone... long day.

---

### Post by gforster on 2009-05-29
You're right, I should have shown my apt-cacher.conf file. I take no offence. Here it is (it is bassically the defaults):

```
#################################################################
# This is the config file for apt-cacher. On most Debian systems
# you can safely leave the defaults alone.
#################################################################

# cache_dir is used to set the location of the local cache. This can
# become quite large, so make sure it is somewhere with plenty of space.
cache_dir=/var/cache/apt-cacher

# The email address of the administrator is displayed in the info page
# and traffic reports.
admin_email=root@localhost

# For the daemon startup settings please edit the file /etc/default/apt-cacher.

# Daemon port setting, only useful in stand-alone mode. You need to run the
# daemon as root to use privileged ports (<1024).
daemon_port=3142

# optional settings, user and group to run the daemon as. Make sure they have
# sufficient permissions on the cache and log directories. Comment the settings
# to run apt-cacher as the native user.
group=www-data
user=www-data

# optional setting, binds the listening daemon to specified IP(s). Use IP
# ranges for more advanced configuration, see below.
# daemon_addr=localhost

# If your apt-cacher machine is directly exposed to the Internet and you are
# worried about unauthorised machines fetching packages through it, you can
# specify a list of IPv4 addresses which are allowed to use it and another
# list of IPv4 addresses which aren't.
# Localhost (127.0.0.1) is always allowed. Other addresses must be matched
# by allowed_hosts and not by denied_hosts to be permitted to use the cache.
# Setting allowed_hosts to "*" means "allow all".
# Otherwise the format is a comma-separated list containing addresses,
# optionally with masks (like 10.0.0.0/22), or ranges of addresses (two
# addresses separated by a hyphen, no masks, like '192.168.0.3-192.168.0.56').
allowed_hosts=*
denied_hosts=

# And similarly for IPv6 with allowed_hosts_6 and denied_hosts_6.
# Note that IPv4-mapped IPv6 addresses (::ffff:w.x.y.z) are truncated to
# w.x.y.z and are handled as IPv4.
allowed_hosts_6=fec0::/16
denied_hosts_6=

# This thing can be done by Apache but is much simpler here - limit access to
# Debian mirrors based on server names in the URLs
#allowed_locations=ftp.uni-kl.de,ftp.nerim.net,debian.tu-bs.de

# Apt-cacher can generate usage reports every 24 hours if you set this
# directive to 1. You can view the reports in a web browser by pointing
# to your cache machine with '/apt-cacher/report' on the end, like this:
#      http://yourcache.example.com/apt-cacher/report
# Generating reports is very fast even with many thousands of logfile
# lines, so you can safely turn this on without creating much 
# additional system load.
generate_reports=1

# Apt-cacher can clean up its cache directory every 24 hours if you set
# this directive to 1. Cleaning the cache can take some time to run
# (generally in the order of a few minutes) and removes all package
# files that are not mentioned in any existing 'Packages' lists. This
# has the effect of deleting packages that have been superseded by an
# updated 'Packages' list.
clean_cache=1

# Apt-cacher can be used in offline mode which just uses files already cached,
# but doesn't make any new outgoing connections by setting this to 1.
offline_mode=0

# The directory to use for apt-cacher access and error logs.
# The access log records every request in the format:
# date-time|client ip address|HIT/MISS/EXPIRED|object size|object name
# The error log is slightly more free-form, and is also used for debug
# messages if debug mode is turned on.
# Note that the old 'logfile' and 'errorfile' directives are
# deprecated: if you set them explicitly they will be honoured, but it's
# better to just get rid of them from old config files.
logdir=/var/log/apt-cacher

# apt-cacher can use different methods to decide whether package lists need to
# be updated,
# A) looking at the age of the cached files
# B) getting HTTP header from server and comparing that with cached data. This
# method is more reliable and avoids desynchronisation of data and index files
# but needs to transfer few bytes from the server every time somebody requests
# the files ("apt-get update")
# Set the following value to the maximum age (in hours) for method A or to 0
# for method B
expire_hours=0

# Apt-cacher can pass all its requests to an external http proxy like
# Squid, which could be very useful if you are using an ISP that blocks
# port 80 and requires all web traffic to go through its proxy. The
# format is 'hostname:port', eg: 'proxy.example.com:8080'.
#http_proxy=proxy.example.com:8080

# Use of an external proxy can be turned on or off with this flag.
# Value should be either 0 (off) or 1 (on).
use_proxy=0

# External http proxy sometimes need authentication to get full access. The
# format is 'username:password'.
#http_proxy_auth=proxyuser:proxypass

# Use of external proxy authentication can be turned on or off with this flag.
# Value should be either 0 (off) or 1 (on).
use_proxy_auth=0

# This sets the interface to use for the upstream connection.
# Specify an interface name, an IP address or a host name.
# If unset, the default route is used.
#interface=

# Rate limiting sets the maximum bandwidth in bytes per second to use
# for fetching packages. Syntax is fully defined in 'man wget'.
# Use 'k' or 'm' to use kilobits or megabits / second: eg, 'limit=25k'.
# Use 0 or a negative value for no rate limiting.
limit=0

# Debug mode makes apt-cacher spew a lot of extra debug junk to the
# error log (whose location is defined with the 'logdir' directive).
# Leave this off unless you need it, or your error log will get very
# big. Acceptable values are 0 or 1.
debug=0

# To enable data checksumming, install libberkeleydb-perl and set this option
# to 1. Then wait until the Packages/Sources files have been refreshed once
# (and so the database has been built up). You can also nuke them in the cache
# to trigger the update.  
# checksum=1

# Print a 410 (Gone) HTTP message with the specified text when accessed via
# CGI. Useful to tell users to adapt their sources.list files when the
# apt-cacher server is being relocated (via apt-get's error messages while
# running "update")
#cgi_advise_to_use = Please use http://cacheserver:3142/ as apt-cacher access URL
#cgi_advise_to_use = Server relocated. To change sources.list, run perl -pe "s,/apt-cacher\??,:3142," -i /etc/apt/sources.list

# Server mapping - this allows to hide real server names behind virtual paths
# that appear in the access URL. This method is known from apt-proxy. This is
# also the only method to use FTP access to the target hosts. The syntax is
# simple, the part of the beginning to replace, followed by a list of mirror
# urls, all space separated. Multiple profile are separated by semicolons
# Note that you need to specify all target servers in the allowed_locations
# options if you make use of it. Also note that the paths should not overlap
# each other. FTP access method not supported yet, maybe in the future.
# path_map = debian ftp.uni-kl.de/pub/linux/debian ftp2.de.debian.org/debian ; ubuntu archive.ubuntu.com/ubuntu ; security security.debian.org/debian-security ftp2.de.debian.org/debian-security

# Permitted package files - this is a perl regular expression which matches all
# package-type files (files that are uniquely identified by their filename). 
# The default is: 
#package_files_regexp = (?:\.deb|\.rpm|\.dsc|\.tar\.gz|\.diff\.gz|\.udeb|index\.db-.+\.gz|\.jigdo|\.template)$

# Permitted Index files - this is the perl regular expression which matches all
# index-type files (files that are uniquely identified by their full path and
# need to be checked for freshness). 
#The default is:
#index_files_regexp = (?:Index|Packages\.gz|Packages\.bz2|Release|Release\.gpg|Sources\.gz|Sources\.bz2|Contents-.+\.gz|pkglist.*\.bz2|release|release\..*|srclist.*\.bz2|Translation-.+\.bz2)$

```

Knowing me, it is probably a very basic problem. Though, when I go to Places>Network it doesn't show me the other computers in the lab (i am able to ping them). Could that have to do with anything. The server is also Win2k3 for active directory (we had windows machines previously). The apt-cacher server is simply the most powerful desktop machine in the lab with the largest hard drive. Does any of that affect anything?

---

### Post by Skip Da Shu on 2009-05-29
While I don't see the connection the error you are getting I am suspicious of:
```
group=www-data
user=www-data
```
I don't recall the apt-cacher install creating this user:group.  I set mine to root on both since I have it running in 'daemon' mode.

On one of the client machines can you enter the [http://uraptcacher:3142/](http://uraptcacher:3142/) into a browser and see the status report?  If not, on teacher can you enter into a [http://localhost:3142/](http://localhost:3142/) and get it?

Can you ping teacher from the client by hostname or do you have to ping by ip?

Please paste the top couple entries in the client's sources.list it sounds like a format problem there (part of the reason I recommend the /etc/apt/apt.conf.d/01proxy method).

I don't understand this: > The server is also Win2k3 for active directory

---

### Post by gforster on 2009-05-29
OK, I changed the settings to root. 

I can reach [http://uraptcacher:3142/](http://uraptcacher:3142/) from the local (host) computer but not from any client.

I can only ping by ip and not by hostname.

I am obviously missing something fundamental, I have not clue what it is.

I have already changed the client's sources.list to its basic self and done the proxy method. But, the one on the host (which I copied to the client) looks like this (I put the whole thing up, just in case and changed my hostname to aptcacher1):

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://aptcacher1:3142/us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://aptcacher1:3142/archive.canonical.com/ubuntu jaunty partner
# deb-src http://aptcacher1:3142/archive.canonical.com/ubuntu jaunty partner

deb http://aptcacher1:3142/security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://aptcacher1:3142/security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://aptcacher1:3142/security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://aptcacher1:3142/security.ubuntu.com/ubuntu jaunty-security universe
deb http://aptcacher1:3142/security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://aptcacher1:3142/security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by gforster on 2009-05-29
to add slightly to the confusion (or maybe to clarify):

now when I ping the hostname I get a reply from a different ip at computerlab.ourschool.org

I am guessing that this has to do with our win2k3 server. 

Also, although I can't put [http://apcacher:3142](http://apcacher:3142) and get anything in a webrowser, it does work with [http://10.host.ip.here:3142](http://10.host.ip.here:3142)

hmmm

---

### Post by Skip Da Shu on 2009-05-29
A couple things...

See this about [**_changing hostnames_**]("http://ubuntuforums.org/showpost.php?p=2042486&postcount=3").

Just to fix the hostname resolution problem I'd go into the test client's /etc/hosts file and add a line to resolve the name of teacher or aptcacher1 (the apt-cacher server machine's hostname).  The example below is from my Ubuntu desktop machine who's name is c17-desktop:
```
127.0.0.1	c17-desktop localhost
127.0.1.1	c17-desktop
192.168.xxx.xx c17-desktop      

# fixed ip servers
192.168.xxx.xxx crunch34
192.168.xxx.xxx crunch20        <--- this is my apt-cacher

# other fixed ip machines
192.168.xxx.xxx	c15-desktop
```

You should now be able to ping the apt-cacher from this machine by hostname.

  
Next, I don't see a problem with your sources.list but I can't recall if using the local hostname in the source.list on the server is right or if it's supposed to point to "localhost".  The file would be fine for a client though.  However, if it were me I'd eliminate that potential and simplify maintenance by also setting it back to 'stock' and adding a /etc/apt/apt.conf.d/01proxy to the server also but it's 01proxy file would need to contain this line:
```
Acquire::http::Proxy "http://localhost:3142";
```
This tells the apt running on the host to go to apt-cacher on localhost (itself) for repository data.  This way an update needed by the OS of the apt-cacher server is cached in case a client later needs it also.

After doing this select System->Admin->Update Manager and tell it to "check" so it'll read the header records and in doing so it should access apt-cacher.  Then...

Take a look at your access log (/var/log/apt-cacher/access.log) and see if it shows anybody having ever got to the cache.  At the end of the file you should see access from 127.0.0.1 (localhost) as a result of the above update check (a good 10 lines or so).

If this all works according to plan then do the 'update' from the test client and see what happens and if anything shows in the access log.  You might also check the /var/log/apt-cacher/error.log

You can ignore this error if it's there:
> Fri May 29 07:48:47 2009|INETD|info [20832]: Warning: no running inetd server found

---

