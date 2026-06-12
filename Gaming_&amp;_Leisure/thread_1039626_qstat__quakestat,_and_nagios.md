---
title: "qstat / quakestat, and nagios"
date: 2009-01-14
forum: Gaming &amp; Leisure
---

### Post by mbradlcu on 2009-01-14
Hi all,
I spent a bunchOtime getting nagios running with the latest svn build of qstat so I'd though I'd post my travels in case anyone else could benefit from them.

Nagios has a very cool plugin that can monitor games using the qstat program. Unfortunately qstat found in the Ubuntu repos is (stable) very old and doesn't support etqw.

Download qstat from svn:
```

svn checkout https://qstat.svn.sourceforge.net/svnroot/qstat/trunk/qstat2 qstat2

```

Move into the qstat directory:
```
cd qstat2
```
Install automake and autoconf
```
sudo apt-get install automake autoconf
```
Start to build qstat:
```
./autogen.sh
```
It fails producing:
> configure.ac: 3: required file `./[gnuconfig.h].in' not found
Makefile.am:29: invalid variable `dist_configfiles_DATA'
I'm sure there's a correct way to do this but this worked for me:
```
cp gnuconfig.h.in "[gnuconfig.h].in"
```
then finish the build:
```

./configure && make && make install

```
1 last thing, nagios expects the executable /usr/bin/quakestat so just link it to the qstat exec:
```
ln -s /usr/local/bin/qstat /usr/bin/quakestat
```

cool, so now qstat is installed with etqw support!

Now to configure the nagios plugin,
```
vi /etc/nagios-plugins/game.cfg
```
here's what my modified game.cfg looks like:
> # 'check_quake1' command definition
define command{
command_name check_quake1
command_line /usr/lib/nagios/plugins/check_game qs $HOSTADDRESS$
}

# 'check_quake2 command definition
define command{
command_name check_quake2
command_line /usr/lib/nagios/plugins/check_game q2s $HOSTADDRESS$
}

# 'check_quake3 command definition
define command{
command_name check_quake3
command_line /usr/lib/nagios/plugins/check_game q3s $HOSTADDRESS$
}

# 'check_quake4 command definition
define command{
command_name check_quake4
command_line /usr/lib/nagios/plugins/check_game q4s $HOSTADDRESS$
}

# 'check_doom3' command definition
define command{
command_name check_doom3
command_line /usr/lib/nagios/plugins/check_game dm3s $HOSTADDRESS$
}

# 'check_etqw' command definition
define command{
command_name check_etqw
command_line /usr/lib/nagios/plugins/check_game etwqs $HOSTADDRESS$
}

# 'check_rws' command definition
define command{
command_name check_rws
command_line /usr/lib/nagios/plugins/check_game rws $HOSTADDRESS$
}

# 'check_unreal' command definition
define command{
command_name check_unreal
command_line /usr/lib/nagios/plugins/check_game uns $HOSTADDRESS$ -P $ARG1$ -p 8
}

# 'check_ut2004' command definition
define command{
command_name check_ut2004
command_line /usr/lib/nagios/plugins/check_game ut2004m $HOSTADDRESS$ -P $ARG1$ -p 8
}

that's it!

---

