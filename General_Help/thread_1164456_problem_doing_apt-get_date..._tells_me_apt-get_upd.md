---
title: "problem doing apt-get date... tells me apt-get update?"
date: 2009-05-19
forum: General Help
---

### Post by hortstu on 2009-05-19
Here's  what the terminal tells me... I've bolded the part tha's perplexing me.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: You may want to run apt-get update to correct these problems
mike@desktop:/$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Fetched 308B in 0s (395B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
**W: You may want to run apt-get update to correct these problems**

Thanks for any help.

---

### Post by zvacet on 2009-05-19
In terminal type 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys  4874D3686E80C6B7
gpg --export --armor  4874D3686E80C6B7 | sudo apt-key add -

---

### Post by hortstu on 2009-05-19
Thanks for the help.  I followed your recommendations but when I type the third command I end up with a blinking cursor and no prompt.  I restarted the terminal and tryed apt-get update again to see if anything changed and I'm getting the same response.

---

### Post by hortstu on 2009-05-19
You still out there zvacet?

---

### Post by hortstu on 2009-05-19
sorry to keep bumping this but I'm afraid it get's overlooked by those just logging on.

---

### Post by SuperSonic4 on 2009-05-19
Type in ```
sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 4874D3686E80C6B7 gpg --export --armor 4874D3686E80C6B7 | sudo apt-key add - && sudo apt-get update
```

FYI: you can cancel most things in terminal by pressing Ctrl+C

---

### Post by zvacet on 2009-05-20
> when I type the third command

There is no third command.You can do it like **SuperSonic4** adviced.

---

### Post by hortstu on 2009-05-20
OK first thanks for being patient with me.

Second I feel like I learned a lot about using the terminal over the last few days but this is really surprising me.

I entered the command supplied by super sonic... thankyou, then of course I'm asked for my password.  I entered it a dozen times but it is incorrect.

So I do sudo apt-get update and then enter my password without a problem. Then I reenter the command supplied by supersonic.

I'm curious why my password wouldn't work with the command but anyway these are the results after I finally got it to work.

> mike@desktop:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 4874D3686E80C6B7 gpg --export --armor 4874D3686E80C6B7 | sudo apt-key add - && sudo apt-get update
gpg: WARNING: unsafe ownership on configuration file `/home/mike/.gnupg/gpg.conf'
gpg: "gpg" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "--armor" not a key ID: skipping
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
gpg: no valid OpenPGP data found.
mike@desktop:~$ 

I'm getting the impression from this that the problem isn't solved

---

### Post by mb_webguy on 2009-05-20
That's because SuperSonic4 goofed in the commands he posted.  There should be either a "&&" or a ";" before "gpg --export".  Copy and paste the commands svacet posted, and you should be fine.  (Please note that these are *two* commands.  If you somehow made them into three commands, you did something wrong.

---

### Post by hortstu on 2009-05-20
Thanks everyone that worked.  Anyone getting the impression from these posts that I shouldn't be messing with the terminal or maybe even linux for that matter?

---

### Post by mb_webguy on 2009-05-20
> **hortstu said:**
> Thanks everyone that worked.  Anyone getting the impression from these posts that I shouldn't be messing with the terminal or maybe even linux for that matter?

Not at all.  We were all newbies at some point.  I don't know about you, but I can still remember the first time I sat down at a computer with a graphical desktop environment and tried to figure out the differences between single- and double-clicks.  (Granted, it's been a while...)

And in general, most things can be done graphically in a modern Linux environment, anyway.  You could have done the above using a GUI interface, but the command line is (usually) much faster, and applicable to all Linux systems -- which is not necessarily the case when following instructions for a desktop environment, since multiple desktops are available for Linux.

---

