---
title: "Desktop Effects Not Working"
date: 2009-05-10
forum: General Help
---

### Post by justin10ec on 2009-05-10
Hello,

I have used Ubuntu in the past and the Desktop Effects have worked fine. It also worked in the 9.04 beta.

My video card is: How do I find his? I know it has used a propriety driver that it's no longer finding?


What should I do?

---

### Post by wiznillyp on 2009-05-10
Someone really needs to make a sticky about this...

What VGA are you using? Some VGAs (lots of Intel stuff) were blacklisted from compiz in 9.04, this is most likely your problem if this worked before.

BTW, Did you search the forums for the "compiz not working"?  There are a ton of threads about this.

---

### Post by justin10ec on 2009-05-10
I know it's Intel, but I don't know which. How do I find this? 

Is there any workaround? I'll probably leave Ubuntu again, if there's not.

---

### Post by raymondh on 2009-05-10
> **justin10ec said:**
> Hello,

I have used Ubuntu in the past and the Desktop Effects have worked fine. It also worked in the 9.04 beta.

My video card is: How do I find his? I know it has used a propriety driver that it's no longer finding?


What should I do?

To find what card you're using, in terminal, type

```
lspci
```

and look for VGA

Regarding "it's no longer finding" ...

I seem to remember a thread the other day wherein the poster managed to solve it by enabling all his third party sources (click all those JAUNTY related). I believe it's at system > administration > software sources. 

Also see if you can activate any drivers.  system > adminitration > hardware drivers

Hope this can help.

---

### Post by justin10ec on 2009-05-10
VGA: 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Still didn't work after enabling the third party sources.

---

### Post by raymondh on 2009-05-10
googling around whilst waiting for your sudo lspci post, have a look at these links ... maybe it can be of help

[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)
[http://webupd8.blogspot.com/2009/05/ubuntu-intel-graphic-card-driver-news.html](http://webupd8.blogspot.com/2009/05/ubuntu-intel-graphic-card-driver-news.html)
[http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

---

### Post by raymondh on 2009-05-10
965 in x3000 and x3100 seems to have been fixed

try

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by justin10ec on 2009-05-10
It still says "Desktop Effects could not be enabled"

---

### Post by justin10ec on 2009-05-10
It seems that I read somewhere that it's blacklisted because of bugs? Does this mean the blacklist isn't permanent?

---

### Post by justin10ec on 2009-05-12
Is anyone going to give any further help?

---

### Post by raymondh on 2009-05-12
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

maybe this thread could give you ideas.  I have seen threads in the forum were compiz was enabled inspite/despite of the blacklist status.... that is if your driver is still blacklisted.  Most of those threads were workarounds and MAY help you. 

Good luck

---

### Post by wiznillyp on 2009-05-12
> **justin10ec said:**
> Is anyone going to give any further help?Did you search for the EXACT string that you posted here?

"Desktop effects could not be enabled"

---

### Post by justin10ec on 2009-05-13
> **raymondhenson said:**
> [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

maybe this thread could give you ideas.  I have seen threads in the forum were compiz was enabled inspite/despite of the blacklist status.... that is if your driver is still blacklisted.  Most of those threads were workarounds and MAY help you. 

Good luck

Alright, I ran that script, this is it's output:

```
Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 
```


What should I do now? I was reading here [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) that it's possible to ignore the blacklist. Should I do this or wait until a fix is available. Will a fix ever be available?

I don't know if this is useful or not, this is what it shows if I type "compiz" in the terminal.

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by Tipped OuT on 2009-05-13
Yes, just by pass the black list (google how to). Be careful though, it's black listed for a reason.

---

### Post by justin10ec on 2009-05-13
> **Tipped OuT said:**
> Yes, just by pass the black list (google how to). Be careful though, it's black listed for a reason.

Okay it's working though. The only thing I notice that isn't working is when you have the highest level on, it usually attaches to the slides of the windows, and it's not doing that. I am happy that part isn't working anyway, I never liked it.

Thanks for all of your suggestions and help. Do you think it'll ever be white listed?

---

### Post by raymondh on 2009-05-13
> **justin10ec said:**
> 

What should I do now? I was reading here [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) that it's possible to ignore the blacklist. Should I do this or wait until a fix is available. Will a fix ever be available?



With my apologies, I cannot recommend whether to "ignore the blacklist" or not.  I have linked the forum threads to show you similarities to your dilemna, but to follow the workarounds is something you will have to decide on your own.  

As I understand, the blacklist is there for a reason (conflicts with x-org, I think).  

Will a fix be available .... I really hope so and i'm confident the devs know our dilemnas and frustrations.

Why not ask around for the actual experiences of those who did the workaround/s?  Maybe that will help you make a decision.  Here's another link if you wish:

[http://ubuntuforums.org/showthread.php?t=1133842](http://ubuntuforums.org/showthread.php?t=1133842)

Good luck.

---

