---
title: "Can someone please tell me what speed you are getting from my ftp server?"
date: 2009-04-14
forum: General Help
---

### Post by jrg_dnn on 2009-04-14
Download this file in firefox (dont have to finish it all)

[ftp://alex1234:alex1234@dd-wrt.myftp.org/videos/edubuntu-8.10-addon-amd64.iso](ftp://alex1234:alex1234@dd-wrt.myftp.org/videos/edubuntu-8.10-addon-amd64.iso)

Let me know if the connection is good and steady, and what the rate is.

Thanks alot

---

### Post by jrg_dnn on 2009-04-14
Bump, It'll only take a few seconds

---

### Post by N_Nick on 2009-04-14
I can't even connect to it but maybe its just my ISP.

---

### Post by dcstar on 2009-04-14
> **jrg_dnn said:**
> Download this file in firefox (dont have to finish it all)

[ftp://alex1234:alex1234@dd-wrt.myftp.org/videos/edubuntu-8.10-addon-amd64.iso](ftp://alex1234:alex1234@dd-wrt.myftp.org/videos/edubuntu-8.10-addon-amd64.iso)

Let me know if the connection is good and steady, and what the rate is.

Thanks alot

0 - it times out.

---

### Post by sekinto on 2009-04-14
```
tony@Norway:~$ wget --ftp-user=alex1234 --ftp-password=alex1234 ftp://dd-wrt.myftp.org/videos/edubuntu-8.10-addon-amd64.iso 
--2009-04-14 02:17:07--  ftp://dd-wrt.myftp.org/videos/edubuntu-8.10-addon-amd64.iso
           => `edubuntu-8.10-addon-amd64.iso'
Resolving dd-wrt.myftp.org... 72.193.200.19
Connecting to dd-wrt.myftp.org|72.193.200.19|:21... failed: Connection timed out.
```

I can't connect. Doesn't work in Firefox either. ;)

---

### Post by jrg_dnn on 2009-04-14
I changes the port to 20001 .

Can someone try it now, Thanks.):P

---

### Post by N_Nick on 2009-04-14
Still nothing.

---

### Post by jrg_dnn on 2009-04-14
If the ftp lnk doesnt work, please try this

[http://dd-wrt.myftp.org:7000/Files/videos/edubuntu-8.10-addon-amd64.iso](http://dd-wrt.myftp.org:7000/Files/videos/edubuntu-8.10-addon-amd64.iso)

username, alex1234

passw: alex1234

---

### Post by N_Nick on 2009-04-14
Ok that worked.

I get 80ish KB/sec.

---

### Post by jrg_dnn on 2009-04-14
Thanks alot N_Nick,  and everyone else that is tried,:guitar:

---

### Post by time_bomb on 2009-04-14
me too.what's wrong with the survice or firefox?

---

### Post by SunnyRabbiera on 2009-04-14
Err no, nothing...
And I have cable internet speed here, I can download a file in Japan without issues, but this is quite slow.

---

### Post by cpetercarter on 2009-04-14
Varies between 20kbps and 120kbps

---

### Post by SunnyRabbiera on 2009-04-14
> **time_bomb said:**
> me too.what's wrong with the survice or firefox?

Its certainly not firefox, trying on opera same deal...

---

### Post by jrg_dnn on 2009-04-14
thanks everyone for trying

---

### Post by mb_webguy on 2009-04-14
I'm getting 204KB/sec on a cable broadband connection.

Btw, I can access all of the files in your video directory without a proper login.  The only file that seems to be protected is the ISO.  I don't know if that's your intention, but I thought you might want to know.  Also, I wasn't actually able to download the ISO, since I apparently entered the login information incorrectly the first time, and thereafter I keep getting the "Incorrect user name or password" page.

---

### Post by eBoxNet on 2009-04-14
also able to change user's pass.
please reconfig your linksys ftp server.

---

### Post by 3Miro on 2009-04-14
210 KB/s from VA USA on Internet connection with up to 350 KB/s. I only downloaded the fist 20MB and at one point the connection dropped to 190, but it went back up. On average it was about 210.

---

### Post by aktiwers on 2009-04-14
150kb/s from Denmark

---

### Post by ju2wheels on 2009-04-14
280kb/s using University network w/ a 900kb/s dl cap.

---

### Post by jrg_dnn on 2009-04-18
Ok, going to change passwd, usernames, and ports, sorry to whoever was downloading stuff from my server :(. I really didnt mind, but i have a 5 Mbps upload connection, and you are barely using 12 KB/s, so its going to take a few months before you are able to download all 3 TB worth of info :)

---

### Post by jrg_dnn on 2009-04-18
Oh wow, it seems like someone is trying to bruteforce, crack my linksys ftp passwords. Lets watch :popcorn:

---

### Post by aktiwers on 2009-04-19
Thats why you shouldnt give out info like that :)

---

### Post by paradigm2 on 2009-04-19
I hope you have ssh and telnet, etc access disabled on this account. :(

I would try the speed test but I have my line throttled at 125Kb/s so as not to interfere with others using my router...so there'd be no point.

---

