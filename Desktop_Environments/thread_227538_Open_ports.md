---
title: "Open ports"
date: 2006-08-01
forum: Desktop Environments
---

### Post by saracen on 2006-08-01
I downloaded nmap and nmapfe and ran a port scan on my system.  I get the following:

```
PORT         STATE SERVICE
631/tcp     open  ipp
55075/tcp open  unknown
55812/tcp open  unknown
```

The first port (631) is for printing so that's cool... but what about the other two?  Does anyone know how I can find out what is opening those ports?

---

### Post by ciscosurfer on 2006-08-01
55075 is reported by some sites as being net/cvsync (do you run cvs?) and 55812 as x11/xlockmore (no clue here)...do some research on these names to get a better idea and search the port numbers as well.  But remember, these ports are in the private/dynamic range and so these ports may have opened up only once for the program that was using them (they may open other ports at other access times).

A good place to go to check your port security is at [ShieldsUp!]("https://www.grc.com/x/ne.dll?bh0bkyd2") and scan your ports this way.  It's a very, very good site, extremely reputable and run by Steve Gibson of SpinRite fame.

---

### Post by saracen on 2006-08-02
ya, i ran a scan again and came up with two different ports this time:

```
PORT      STATE SERVICE
631/tcp   open  ipp
37955/tcp open  unknown
40448/tcp open  unknown
```

The reason I'm checking really is because say that someone has somehow managed to get something malicious on my machine - i want to know if that program is making connections to the outside world.  

What's the best way to find out if your system is clean.  Most people say that virus scanners aren't necessary for linux, but i've tried experimenting with various pieces of software and I just want to give my setup a clean bill of health.

---

### Post by ciscosurfer on 2006-08-03
Use a hardware firewall/router and lock it down (should be locked pretty good out of the box, but you can make it even more solid by tweaking certain settings within the firewall/router).  That's really the best way b/c you can literally prevent specific ports or ranges of ports from accessing the internet and vice versa.  It's a wise investment.  You won't be sorry and it's money well-spent.

---

### Post by saracen on 2006-08-03
> **ciscosurfer said:**
> Use a hardware firewall/router and lock it down (should be locked pretty good out of the box, but you can make it even more solid by tweaking certain settings within the firewall/router).  That's really the best way b/c you can literally prevent specific ports or ranges of ports from accessing the internet and vice versa.  It's a wise investment.  You won't be sorry and it's money well-spent.

Ya, but I'm saying that now, after the fact that I have installed various pieces of software, I'd like to "clean" my system - make sure that there is nothing malicious on it.  Is a linux antivirus tool really going to do the job for me?

---

### Post by ciscosurfer on 2006-08-03
If you're that worried, backup the files you want to keep and then reinstall your system and start fresh.

---

### Post by saracen on 2006-08-03
I'm not looking to do that.  In Windows (and I'm not advocating that windows is better) you can clean your system after an infection - be it a virus, spyware, adware, rootkit, whatever.  In Linux I'd like to know if there is software that checks my system and can give it a clean bill of health - free of all that crap.  For example, I know that in windows a lot of the time the spyware removal tools flag some cookies as being spyware.  I don't know whether that is true or not, but it removes them in any case.  I know that the same cookies get downloaded on Linux but there is no tool that I know of to remove them.

---

### Post by harisund on 2006-08-03
Do a ```
sudo netstat -plant
sudo netstat -plant | grep LISTEN
``` to get an idea of what is listening on those ports. Might not be something malicious after all. 

Ubuntu comes with no ports open by default. Have a look.

---

### Post by ciscosurfer on 2006-08-03
You can delete cookies from within your browser.  Or, you can delete them by going to its respective hidden folder within your home folder.  

Also, follow **harisund's** advice above.

If you are looking for security tools, [here is good place to start]("https://help.ubuntu.com/community/InstallingSecurityTools").  

For example, download chkrootkit to see if you system has been comprised by a rootkit, i.e., do a sudo apt-get install *pick_your_weapon_of_choice*```
sudo apt-get install chkrootkit
sudo chkrootkit
```

---

