---
title: "bash: file not found - yet it is there"
date: 2009-02-21
forum: General Help
---

### Post by ThaddeusW on 2009-02-21
Ok I had this problem a while ago and now I have it again. I downloaded baudline ([http://www.baudline.com](http://www.baudline.com)) and untar'd it. I tried to run it but typing ./baudline and bash just tells me:

bash: ./baudline: No such file or directory

What is wrong here? It was already marked as executable and I even tried to sudo chmod +x baudline but it still says file not found. I even tried to copy it to /usr/bin and still no luck. Now I have been running Linux for a while and had this problem only once and I forgot what I did to fix it. The system is a fresh install of Kubuntu 8.04 with KDE 3. I rsync'd it to my Linux server with basix xorg/fluxbox desktop. It ran fine after i installed the missing libxp.  

How can bash not see the file to execute it yet rsync, vim and less can manipulate/view the file just fine? Even trying to double click it under Dolphin does nothing. 

Any ideas?

---

### Post by dcstar on 2009-02-21
> **ThaddeusW said:**
> Ok I had this problem a while ago and now I have it again. I downloaded baudline ([http://www.baudline.com](http://www.baudline.com)) and untar'd it. I tried to run it but typing ./baudline and bash just tells me:

bash: ./baudline: No such file or directory

What is wrong here? It was already marked as executable and I even tried to sudo chmod +x baudline but it still says file not found. I even tried to copy it to /usr/bin and still no luck. Now I have been running Linux for a while and had this problem only once and I forgot what I did to fix it. The system is a fresh install of Kubuntu 8.04 with KDE 3. I rsync'd it to my Linux server with basix xorg/fluxbox desktop. It ran fine after i installed the missing libxp.  

How can bash not see the file to execute it yet rsync, vim and less can manipulate/view the file just fine? Even trying to double click it under Dolphin does nothing. 

Any ideas?

```
uname -m
file baudline
```

If one is a 32-bit and the other 64-bit, then you may have an answer.

---

### Post by Agent ME on 2009-02-21
To above post: If it was the wrong processor architecture for his system, then it wouldn't fail to find the file.

Are you in the same directory as the file 'baudline'? If the file baudline is in your Desktop folder, you need to do "cd Desktop" on the terminal first, etc.

---

### Post by ThaddeusW on 2009-02-22
Thanks so much guys. I have an amd-64 system and somehow I thought it was 32-bit. I feel silly now :(. 

uname -m spit out amd-64 and since I installed kubuntu through netboot via pxe I thought it had the 32 bit net boot files. I actually had the 64 bit net boot files on the tftp server. The whole time I though I had installed the 32-bit version lol.

---

### Post by holzfreiweiss on 2011-03-17
yep, if you have a 32 bit application (e.g. java) but a 64 bit Linux, then you receive a "Bash: file not found"  (just experienced)

Very weird, but true..!

---

### Post by SeijiSensei on 2011-03-17
> **holzfreiweiss said:**
> yep, if you have a 32 bit application (e.g. java) but a 64 bit Linux, then you receive a "Bash: file not found"  (just experienced)

Very weird, but true..!
My guess is that it's not finding some required 32-bit libraries.  

There's a 64-bit version of baudline on that site, too.  Does that fix your problem?

---

