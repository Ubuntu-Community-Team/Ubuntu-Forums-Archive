---
title: "Homepage Hijack?"
date: 2005-04-26
forum: Desktop Environments
---

### Post by spencer on 2005-04-26
Hello,

I  installed gdesklets last night and was trying out the different desklets, calendar, clocks, weather, and toolbar/launchers. I was particularly interested in starterbar which I have read, others have had problems with. It seems a little troublesome for me too. Anyhow, I have two questions. 

1. Is it a security risk to run the desklets and starterbar?
2. My homepage has changed since using gdesklets to the following [http://www1.umn.edu/twincities/index.php](http://www1.umn.edu/twincities/index.php). This wasn't my original homepage and it concerns me. Has anyone has had a similar experience using gdesklets? Does anyone have any other thoughts as to why my homepage changed?

Thank you,

-spencer

---

### Post by spencer on 2005-04-26
It's fixed, using this post [http://ubuntuforums.org/showthread.php?t=29966](http://ubuntuforums.org/showthread.php?t=29966) 
In the properties of firefox launcher I changed "firefox %u" to "firefox" and that was the fix. This still leaves me wondering though, what else happens behind the scenes with starterbar and gdesklets. It definitely uses a lot of cpu power. I'll continue to use it for now and watch for anything unusual. 

Thank you,

-spencer

---

### Post by Jmonti on 2005-09-13
I came here today to also "warn" people of this. I found that if you install starterbar, and then drag firefox from App/Internet down to the starterbar, it uses a pre-configured "advanced" option which hijacks your homepage. I was outraged to see this! This does not look to me like a Bug, but an underhanded way of getting traffic to that site. Think for instance if it directed you to a site that could install software on your PC without you knowing it! You'd be hit before you knew what had happened. As the post above says, you can dissable it by editing the starter by right clicking it and edit starter. Go to the advanced tab and delete the script there as well. 

I'm not happy to this this happen......

---

### Post by angkor on 2005-09-13
[QUOTE=Jmonti]Think for instance if it directed you to a site that could install software on your PC without you knowing it! You'd be hit before you knew what had happened.[/QUOTE]

Erm, this isn't windows we're talking about. Websites will not be able to install anything on your comp unless you tell them to. The %u parameter is just some "I'm feeling lucky" Google feature. A bit strange yes, but nothing to worry about.

---

### Post by Jmonti on 2005-09-14
[QUOTE=angkor]Erm, this isn't windows we're talking about. Websites will not be able to install anything on your comp unless you tell them to. The %u parameter is just some "I'm feeling lucky" Google feature. A bit strange yes, but nothing to worry about.[/QUOTE]

True enough, but I also found text under the advanced tab which directed firefox to that site. It was that "script" I was more upset about than the %u argument.

I understand Linux is better hardened against malware, but what if it sent you ( or a kid) to a porn site instead of a school? I just feel we should try to get this corrected in some way.

---

### Post by Spano on 2005-09-14
For what it's worth, I got the same redirect after installing Sethnakht miniFox 0.5 theme onto Firefox in XFce.  I have no problem with this theme in Gnome.

---

