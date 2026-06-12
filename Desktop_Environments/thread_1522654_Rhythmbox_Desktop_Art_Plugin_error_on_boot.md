---
title: "Rhythmbox Desktop Art Plugin error on boot"
date: 2010-07-02
forum: Desktop Environments
---

### Post by frogotronic on 2010-07-02
Hello,

I'm using the desktop art plugin in rhythymbox, which requires compiz.  Every time I boot (or login), I get an error that says, "**You are not running under a composited desktop-environment. The Desktop Art Plugin cannot work without one.**"

The problem is that rhythmbox is starting *before* compiz loads. How can I delay the start of rhythmbox?

Thanks,
CH

P.S.  I tried delay scripts and they don't (didn't) work.

---

### Post by stinkeye on 2010-07-02
> **cement_head said:**
> Hello,

I'm using the desktop art plugin in rhythymbox, which requires compiz.  Every time I boot (or login), I get an error that says, "**You are not running under a composited desktop-environment. The Desktop Art Plugin cannot work without one.**"

The problem is that rhythmbox is starting *before* compiz loads. How can I delay the start of rhythmbox?

Thanks,
CH

P.S.  I tried delay scripts and they don't (didn't) work.


Save this as **start_rhythmbox**. **[COLOR="Red"]You must enable the Dbus plugin in ccsm.[/COLOR]**
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
                DISPLAY=:0.0 rhythmbox >/dev/null 2>&1 &
                
                 
		done="true";
	else
		echo "rhythmbox is waiting"
		done="false"
		sleep 5;
	fi
done
exit 0
```
Make executable...right click >properties > permissions > execute
Link to it as the command in startup applications.
This will check for compiz and won't start rhythmbox until compiz is loaded.

---

### Post by frogotronic on 2010-07-02
@stinkeye

Thanks!  That did it.  Love the signature, how'd you do the upside down writing?

- CH

---

### Post by stinkeye on 2010-07-03
> **cement_head said:**
> @stinkeye

Thanks!  That did it.  Love the signature, how'd you do the upside down writing?

- CH

No problem. Numerous sites will flip text.
Eg [http://www.fliptext.org/]("http://www.fliptext.org/")
[IMG]http://img821.imageshack.us/img821/2325/eek1.png[/IMG]

---

### Post by TheDexter1111 on 2010-09-29
hey guys, sorry to revive this thread.. but i got the same problem but that script didnt work for me...

i'M running Ubuntu 10.04 with compiz

I even stopped rhythmbox from auto starting altogether but still messes around with my DE.

here is my thread [http://ubuntuforums.org/showthread.php?p=9903445#post9903445](http://ubuntuforums.org/showthread.php?p=9903445#post9903445)

---

### Post by frogotronic on 2011-10-04
Hi,

  You're implementing the script incorrectly.:

Here's how to use the script:

1) Download the script and make it executable.

2) Put it in your home directory.  I called it ".rhythmbox_check.sh"

3) Close rhythmbox

4) System>Preferences>Startup Applications.  Choose the "Options tab".  Uncheck the "Automatically remember running applications when logging out".  Then click on the "Remember Currently Running Application"

5)  Go back to the Startup Programs TAB.

6) Make a new entry.  Call it "Rhythmbox Start check" or anything that makes sense to you.  For the Command, browse to your ".rhythmbox_check.sh" script.  Save & close

Logout and this should work.

- CH     :guitar:

---

