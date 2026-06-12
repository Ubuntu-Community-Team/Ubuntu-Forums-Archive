---
title: "Seting Unreal tournament 2004 dedicated server as a service un ubuntu"
date: 2007-09-21
forum: Gaming &amp; Leisure
---

### Post by jdarias on 2007-09-21
Hello.
<justkidding>We all at the office were too happy when we installed a dedicated server of ut2004 as a service in a dirty dusty cpu... now the server (and the current game)  never go away when the boss comes in ;)</justkidding>. The problem is, [there is a nice how-to in unrealadmin written for windows]("http://http://wiki.unrealadmin.org/Running_a_Server_as_a_Windows_Service_%28UT2004%29"), but nearly no info for doing the same in linux.
Googling around the subject i found a script in gentoo that seems to do the job there (google ut2004-ded)
Does that work in ubuntu? how do i set it? 
here is the script i found:
```
#!/sbin/runscript 

# UT2004 Dedicated Server Runscript by Ken Smith 

# Change the following two variables to customize this script.  The default
# script starts up a Onslaught Server.
# Goto http://www.unrealadmin.org to learn how to edit your options

UCCDIR="GAMES_PREFIX_OPT/ut2004-ded/System"
OPTIONS="server ONS-Torlan?game=Onslaught.ONSOnslaughtGame ini=Default.ini log=server.log -nohomedir"

### Do not edit below here or the world will explode ###

depend() {
	need net
}

start() {
	ebegin "Starting UT2004 Dedicated Server"
	cd ${UCCDIR}
	start-stop-daemon --chdir ${UCCDIR} --env PWD=${UCCDIR} --make-pidfile --start --quiet --pidfile /var/run/ucc-bin.pid --exec ucc-bin -- ${OPTIONS} >> /dev/null &
	eend $? "Failed to start UT2004 Dedicated Server"
}

stop() {
	ebegin "Stopping UT2004 Dedicated Server"
	start-stop-daemon --stop --quiet --pidfile /var/run/ucc-bin.pid -- >> /dev/null
	eend $? "Failed to stop UT2004 Dedicated Server"
	sleep 1
} 

reload() { 
	if [[ ! -f /var/run/ucc-bin.pid ]] ; then
		eerror "UT2004 Dedicated Server isn't running"
		return 1
	fi 
	ebegin "Reloading UT2004 Dedicated Server"
	kill -HUP `cat /var/run/ucc-bin.pid` &>/dev/null
	eend $?
}
```

---

### Post by jdarias on 2007-09-22
bump

---

### Post by ph3ar on 2008-03-29
Any progress?

---

