---
title: "Alter screen position"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Matt73 on 2005-10-16
I have 3 operating systems installed in one box.  Windows 98, Windows 2000 and Ubuntu.  When I boot Ubuntu the screen position is off to the extreme right.  If I alter it's position with my monitor settings everything is OK.  However if I then boot up either of my Windows OS my screen settings are wrong and I have to adjust my monitor again.  

Is there a way I can alter the screen position settings with Ubuntu?  I've googled and searched this forum for an answer but can't find one.   

Thanks.

---

### Post by heimo on 2005-10-16
Open terminal, run xvidtune, adjust position and hit *Show *which will output a modeline to terminal window. Copy paste this to /etc/X11/xorg.conf Monitor section, using
```
sudo gedit /etc/X11/xorg.conf
```
restart X by hitting ctrl+alt+backspace. That should do it. :)

---

### Post by Matt73 on 2005-10-16
Thanks for the response.

My monitor section in the file you mentioned looks like this :-

	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60

My xvidtune output looks like this :-

"1024x768"     65.00   1024 1092 1228 1352    768  775  781  814 -hsync -vsync

Could you please tell me what I enter in the file?

Thank.

---

### Post by heimo on 2005-10-16
[quote=Matt73]Thanks for the response.

My monitor section in the file you mentioned looks like this :-

    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60

My xvidtune output looks like this :-

"1024x768"     65.00   1024 1092 1228 1352    768  775  781  814 -hsync -vsync

Could you please tell me what I enter in the file?

Thank.[/quote]

You should put this:
Modeline "1024x768"     65.00   1024 1092 1228 1352    768  775  781  814 -hsync -vsync
But your HorizSync range looks a bit narrow. Actually, so does the VertRefresh. Here's some additional instructions:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Matt73 on 2005-10-16
Thankyou.  

I inserted modeline as you stated and it works!  I tried it and it turned out that the settings wern't too narrow after all...

Another thing.  When first I boot Ubuntu the initial bootup display is also out sync like the refresh is wrong or something.  Is there a way I can alter this also?

Thanks.

---

### Post by poofyhairguy on 2005-10-17
This is not a forum for problems, its a forum for guides. 

So I moved it.

---

### Post by heimo on 2005-10-17
Poofy: Thanks, I didn't notice.

[quote=Matt73]
Another thing. When first I boot Ubuntu the initial bootup display is also out sync like the refresh is wrong or something. Is there a way I can alter this also?
[/quote] 
What do you mean with initial bootup display? Do you mean the screen where you enter username and password? In that case, maybe this could help:
[http://ubuntuforums.org/showpost.php?p=253944&postcount=3]("http://ubuntuforums.org/showpost.php?p=253944&postcount=3")
[URL="http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21"]
[/URL]

---

### Post by Matt73 on 2005-10-17
Sorry.  I didn't know what section was appropriate.

---

### Post by Pablo_Escobar on 2005-10-17
Check the refresh rates in Win and Ubuntu. 
It can be easily done if You have OSD on Your CRT or LCD monitor.
It'll probably be about 50Hz - 100Hz. These must match in Win and Ubuntu.

EDIT : Heck, I didn't see it was already solved ...... dooooh :)

---

