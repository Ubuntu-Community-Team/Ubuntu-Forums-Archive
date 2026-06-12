---
title: "Pathetic Download Speed of Azureus!"
date: 2006-03-07
forum: Desktop Environments
---

### Post by psypher on 2006-03-07
Hey guys, I really hope you can help, I am very frustrated. I have a lot of issues with Azureus on Ubuntu. I don't know if it's my PC cos my work PC works just fine by installing it with the Automatix script.
But at home I have trouble.

I have everything perfectly setup, NAT'ting is correct, have both UDP and TCP ports forwarded. I have tried various different ports, 6881 (not recommended by azureus anymore), 21, 49000 and now I am on 8080.  I have an IPCop 1.4.10 fw on 512 ADSL. and as far as I can tell the FW is not the issue as my house mate is running WinXP with Azureus and he has perfect downloads, he is on port 443.

I made sure my ratio is good by doing some seeding (2.5), even though my house mate has poor ratio and still gets 512 kbps. i have uninstalled the automatix azureus and installed latest version from the sorceforge site (2.4.0.0) and there was absolutely NO change. 

As fas as I know my Java is fine as all other java aps works ok, I am on 1.5.0_06

I have tried lots of torrents, a few torrents, any combination of torrents and still my d/l sucks, never get over 10k. My torrents mostly are very good, lots of seeds, lots of peers. I am at wits end please can somebody help, this is so very annoying. 

PC
AMD Athlon 2400+
768MB Ram
500GB HDD
my point is it's not a slow PC. 

Thanks for any help

---

### Post by Corvillus on 2006-03-07
Are you certain you're running Azureus with the Sun VM and not the GCJ one, because if you aren't it will always behave as though you're firewalled for some reason. If you've installed the Sun VM, make sure it's the default by running ```
sudo update-alternatives --config java
``` Also, if your upload speed is really poor after this and you are certain your ports are open, it could be packet shaping by your ISP. This site [http://azureus.aelitis.com/wiki/index.php/Bad_ISPs](http://azureus.aelitis.com/wiki/index.php/Bad_ISPs) has more info on that.

---

### Post by psypher on 2006-03-07
I know for a fact that I am running Sun's Java, our company intranet is Java 1.5 only and it works perfectly but here is the output you requested confirming that:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java
      4        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

I pressed enter

And like i said my house mate, in the same house, on the same adsl line, through the same swtich and firewall with exactly the same config, other than he uses port 443, WinXP and I 8080, Ubuntu Breezy (i have tried switching them around and no difference) gets almost always  512kbps d/l. even if he is not even using the line I still only get 100kbps. We are not shaped, I gaurentee that. it's not the ISP. ONLY azureus is slow, i still get 512 through ftp/http/scp/etc...

thanks for that sun alternate command, didn't know that existed.

---

### Post by tbresson on 2006-03-07
My workaround was to download and install Java to /usr/java/
and then edit the azureus script file and change the path of javadir to where I installed Sun's java, e.g. /usr/java/jre_1.5_06/bin

something like that anyway.

I couldn't get azereus to even install a plugin without this change.

It works great now.

---

### Post by psypher on 2006-03-07
Where do I find the azureus script? after installing java from the automatix script and still no d/l's, I did update it with the jre package from sun. There was no problem installing azureus, just getting a decent d/l's

I used to have these issues on Hoary but then I upgraded my java and azureus and all was ok. Re-install breezy and back to square one.

---

### Post by tbresson on 2006-03-08
The script you need to edit is the same script you execute when starting Azureus.

---

### Post by MacV on 2006-03-08
Ok, stupid question. Why are you using port 8080? Isn't that "only" for the general internet applications like your browser?

---

### Post by psypher on 2006-03-08
K I know I said I am not shaped by my ISP, but technically I am. But our ISP's in SA are not too clued up and don't detect P2P traffic just shape P2P ports, so we change ports and like i said my house mate on the same line nails it at the full capacity so in my eyes we are not shaped. So he uses 443 and I use 8080 and since I have no services running on my network on either of those ports and the chances of our ISP shaping web traffic is minimal there is no reason not to use those ports. But like i said I have tried 443, 8080, 6881, 49000, 21 and 22 and no joy. On hoary I ran fine on 8080 for months, although it took me many updates of azureus and java to get it right eventually.  

If you have a good suggestion for ports then I would love to try that. I am willing to try anything except a reinstall, cos: UBUNTU IS NOT WINDOWS ;) God I love Linux :)))

---

### Post by psypher on 2006-03-17
OK so i tried inserting the java directory value in the azureus script but still no difference. So can anybody help me to COMPLETELY remove azureus and java and any kind of reference to it so that I can start this all from the beginning. I am still not keen to re-install ubuntu but I am really at wits end. I don't know why this would be such a mission. 

any help would be greatly appreciated, I have these issues with azureus quite often on many different hardware systems. thanks

---

### Post by Sunnz on 2006-03-17
Do you HAVE to use Azureus??? If not, try BitTornado, shouldn't take that long to install, and you'll can see if it is a problem of Java, or if it is problem your installation of Linux.

---

### Post by psypher on 2006-03-17
I guess not, I just like the advance features that azureus has. I will defenitely give it a try. Just annoying that an application works on windows and not seamlessly on ubuntu. One more point to M$ which shouldn't be that way.

---

### Post by Sunnz on 2006-03-17
Well I myself liked the simplicity of bitTornado, but I can understand how you like the advanced features of Azureus... but yea, at least you can narrow down the problem a bit.

---

### Post by rattking on 2006-03-17
have you tried limiting your upload?  
from theres site

[http://azureus.aelitis.com/wiki/index.php/Increase_download_speed](http://azureus.aelitis.com/wiki/index.php/Increase_download_speed)
it is best not to set it to use all of your upstream capacity. Rather, it is best to set it to use a maximum of 80% of your total upstream bandwidth.

hope it helps

---

