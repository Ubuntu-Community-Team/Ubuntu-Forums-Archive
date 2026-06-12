---
title: "GOTOWEBINAR CITRIX  help?"
date: 2009-05-22
forum: General Help
---

### Post by ukripper on 2009-05-22
Tried running a citrix webinar which didnt work under Linux firefox. i think i will try again and find out if i can do something about it.

Here is the webinar I need regularly - [https://www1.gotowebinar.com/webinar/pre/faq9.tmpl](https://www1.gotowebinar.com/webinar/pre/faq9.tmpl)

I wonder if anyone knows how to make it work under ubuntu?????

Your help is much appreciated!

---

### Post by KhurramM on 2009-05-22
Be specific. U wanna run flash or what type of stream on your PC?

---

### Post by ukripper on 2009-05-22
Can't be more specific than my original post which also contains a link.

cheers.

---

### Post by quinnten83 on 2009-05-22
the requirements say that you need windows or mac.
My guess is that linux is again left in the dark.
You can try with wine, perhaps using firefox under wine, but other than that, I think you are SOL.

---

### Post by ukripper on 2009-05-22
> **quinnten83 said:**
> the requirements say that you need windows or mac.
My guess is that linux is again left in the dark.
You can try with wine, perhaps using firefox under wine, but other than that, i think you are sol.

SOL? What is that?

---

### Post by javathecat on 2010-10-23
This is a problem for me also. I find it a little frustating that these guys only consider windows and mac.
:mad:


I would like to see an easy way to solve this problem also.


Really when you access the webinar the information about your OS is contained in your browser header. I don't really see what the difference would be apart from that.

---

### Post by TrinitronX on 2011-07-20
I tried using firefox under wine, spoofing user agent to both Windows or Mac, and nothing worked :-(

The Citrix installer did work, but the go2webinar launch fails

---

### Post by seawolf167 on 2011-07-20
Were you able to get Citrix working ok? I made a how-to for Citrix a week or so ago with install details [here]("http://ubuntuforums.org/showthread.php?p=11019102#post11019102").

Do you have any errors or anything when trying to access the webinar or it just doesn't load?

---

### Post by mrmedia on 2011-07-21
g2m_download.exe  gets G2MCoreInstExtractor.exe to %temp% in windows
But when running under wine the response is "no arguments supplied" 
So maybe ..........   But then noticed
%temp% also has a CitrixLogs folder and alot of files get copied to
"C:\Program Files\Citrix\GoToMeeting\723"
So maybe best way is to run those under wine.

---

### Post by mrmedia on 2011-07-21
Another avenue maybe 

[http://www.mcfarland.k12.wi.us/citrix/icaweb/en/ica32/setup.htm](http://www.mcfarland.k12.wi.us/citrix/icaweb/en/ica32/setup.htm)
[http://www.agaveblue.org/howtos/Citrix_ICA_How-To.shtml](http://www.agaveblue.org/howtos/Citrix_ICA_How-To.shtml)

This runs okay under wine, but not sure it is the same thing and if interface is enabled.

NB - but there is a native linux version too (if the connection is allowed)
[http://www.agaveblue.org/howtos/Citrix_ICA_How-To.shtml](http://www.agaveblue.org/howtos/Citrix_ICA_How-To.shtml)

---

