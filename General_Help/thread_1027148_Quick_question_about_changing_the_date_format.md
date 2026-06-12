---
title: "Quick question about changing the date format"
date: 2008-12-31
forum: General Help
---

### Post by b3n0 on 2008-12-31
Hey guys,
I'm trying to change the date format from mm/dd/yy to dd/mm/yy.
I found a useful tutorial [here]("http://ubuntuforums.org/showthread.php?t=113018&highlight=gnome+date+format").
However I cant find the file that I need to 'sudo gedit'.
Any ideas as to where It's hiding?
Thanks,

---

### Post by dcstar on 2008-12-31
> **b3n0 said:**
> Hey guys,
I'm trying to change the date format from mm/dd/yy to dd/mm/yy.
I found a useful tutorial [here]("http://ubuntuforums.org/showthread.php?t=113018&highlight=gnome+date+format").
However I cant find the file that I need to 'sudo gedit'.
Any ideas as to where It's hiding?
Thanks,

This post has the command you are supposed to use:

[http://ubuntuforums.org/showpost.php?p=630735&postcount=3](http://ubuntuforums.org/showpost.php?p=630735&postcount=3)

---

### Post by b3n0 on 2008-12-31
This is the part I stumble on.
'Applications - System Tools - Configuration Editor'.
I don't have that

---

### Post by unutbu on 2009-01-01
Hi b3n0, thanks for the interesting link. I did not know about this.

I tried it just now, and this is what I did to make it work:

At a terminal type
```

gconf-editor
```

Navigate to /apps/panel/applets/clock_screen0/prefs

Change the custom_format and format fields.

Log out, and log back in to make the change effective.

---

### Post by TopEnder on 2009-01-01
I think you need to go to: Applications / Add/Remove / System Tools place a tick in the Configuration Editor.  At the Top of this page in Show - select "All Available Applications" hope it helps.

---

### Post by abn91c on 2009-01-01
you** don'[COLOR="Red"][/COLOR]t **need to edit any files ubuntu has a GUI for that, it is in the gnome control center under regional settings, there is a tab for the time/date format.

---

### Post by b3n0 on 2009-01-01
> **unutbu said:**
> Hi b3n0, thanks for the interesting link. I did not know about this.

I tried it just now, and this is what I did to make it work:

At a terminal type
```

gconf-editor
```

Navigate to /apps/panel/applets/clock_screen0/prefs

Change the custom_format and format fields.

Log out, and log back in to make the change effective.

You rock!!
That worked, thanks. +1

---

### Post by dcstar on 2009-01-01
> **abn91c said:**
> you** don'[COLOR="Red"][/COLOR]t **need to edit any files ubuntu has a GUI for that, it is in the gnome control center under regional settings, there is a tab for the time/date format.

My 8.04 Gnome Control Center does not have that option, and neither has my 8.10 system.

---

### Post by cokeonice on 2009-01-01
> **TopEnder said:**
> I think you need to go to: Applications / Add/Remove / System Tools place a tick in the Configuration Editor.  At the Top of this page in Show - select "All Available Applications" hope it helps.

My Ubuntu is setup just like that but I still do not have the Applications > System Tools > Configuration Editor.

---

### Post by b3n0 on 2009-01-01
This is what solved it for me.
In terminal type
```
gconf-editor
```
It should pop up with the 'configuration editor' screen.
Navigate like so...  apps > panel > applets > clock_screen0 > prefs
Double click 'custom format', a small window should pop up.
I put the following in.
```
%a %e %b, %H%M
```
Where %a = short day of the week (mon, tue, wed... etc)
%e = date (1-31) 
%b = short month (Jan, Feb, Mar... etc)
%H = hours (24 hour format)
%M = minutes
[URL="http://au2.php.net/strftime"]
Here is a useful link that will give you the code for the format you desire.[/URL]

You can add the following to seperate you Date and time to customise the format however you like... 
/ = slashes
. = full stops
, = commas 
etc

Click ok,

Back in the configuration editor, edit the format attribute. Clear whatever is there and type in
```
custom
```
Click ok, and close the configuration editor.

It may take a restart to kick in.
You're done!

---

### Post by AbdulRahiem on 2009-01-21
Thank you. This worked well. My clock applet now shows (almost) the ISO format: yyyy-mm-dd hh:mm:ss.

Two questions remain, though:

[LIST=1]
[*]How can I get the calender displayed sun-sat instead of mon-sun?
[*]How can I apply my custom date format to the message folders in evolution? They show mmm dd yyyy with no time, unfortunately. The calendar there is correctly sun-sat, because I found its own setting for it. But I have not found a setting for the date format.
[/LIST]
Best regards

---

