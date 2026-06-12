---
title: "Quake4 XQF unable to connect?"
date: 2005-10-22
forum: Gaming &amp; Leisure
---

### Post by equilibrium on 2005-10-22
I seem to be having problems connecting to servers on quake4. All I get when I try to connect using XQF is ""this server is not compatible with the version of quake4 you have installed" if I tell it to launch anyway it seems to try to connect but it just ends  up back at the menu screen?

I'm not sure if it's a problem with the linux client or not as I seem to be able to connect on windows :( also these servers don't seem to appear on the in-game browser :(.

the servers are multiplay.co.uk servers and jolt.co.uk servers :(

213.208.119.120:28004
85.236.101.77:29104

---

### Post by arcanistherogue on 2005-10-22
I got the same sort of errors with XQF.  Also, I only got about 230 servers on XQF, and I upgraded to the new XQF to see more than 1000 Quake 4 servers.

---

### Post by equilibrium on 2005-10-22
I was playing on multiplay and jolt on windows before so I guess it's a linux problem? as I have also tried connecting to them manually and it still doesn't seem to connect. I think PB is picking up the linux commands? as the alsa etc commands seem to be red when I scroll up the console lol :( :rolleyes:

I think the mismatch in versions is there because the servers are windows :(

---

### Post by equilibrium on 2005-10-22
here's a condump:

```
Sending challenge to 85.236.101.77:28504

received challenge response 0x200d5bff from 85.236.101.77:28504

sending connect to 85.236.101.77:28504 with challenge 0x200d5bff

Waiting for authorization

sending connect to 85.236.101.77:28504 with challenge 0x200d5bff

The pure server at 85.236.101.77:28504 didn't provide a reference to executable code
```

---

### Post by crane on 2005-10-23
It's a compatibility issue. The windows release is build 2142 and the linux release is puild 2147.12.
It seems to be ID's mistake but I have yet to find a work around. I just purchased a server from clan servers. They installed the thing on a windows computer so now I have a server I can't play on:evil:

---

### Post by seethru on 2005-10-23
[QUOTE=crane]It's a compatibility issue. The windows release is build 2142 and the linux release is puild 2147.12.
It seems to be ID's mistake but I have yet to find a work around. I just purchased a server from clan servers. They installed the thing on a windows computer so now I have a server I can't play on:evil:[/QUOTE]
wow, that sucks...did you ask them if they can put it on a linux machine?

---

### Post by yqiang on 2005-11-02
check [http://skuld.bmsc.washington.edu/~yi/blog/?p=7](http://skuld.bmsc.washington.edu/~yi/blog/?p=7) for a fix.

---

