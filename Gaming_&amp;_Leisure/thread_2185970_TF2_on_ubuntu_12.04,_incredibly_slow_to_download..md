---
title: "TF2 on ubuntu 12.04, incredibly slow to download."
date: 2013-11-05
forum: Gaming &amp; Leisure
---

### Post by lithiumKid1976 on 2013-11-05
hi

i just wanted to see if any one else was experiencing the same issue as me.
TF2 on 12.04 is taking an age to download.

my broadband isnt the best, but download time is showing 1 day or longer. (way longer then it took on windoze)
the regional setting are correct on steam.

also, it doesnt seem to remember how much i have downloaded. for example, if i stick with it one day, and download gets to 20%, if i close off steam, and try to download a bit more , it goes back to 0%....

machine is dual booting win7 / ubuntu 12.04 on a SSD

steam folder is redirected to a 250GB hard disk.

any advice appreciated.
thanks
D.

---

### Post by CRAlmsFan on 2013-11-05
I myself have a modest connetion. 22 up and 2 down. I had been running wireless and to download TF2 took about 2 1/2 to 3 hours over the wireless. That didn't bother me so much but the nasty ping spikes while playing was horrible. My average ping is around 42-44  on my favorite server. But would spike to over 300 every 20 seconds or so. I finally had the chance to hard wire and that whole issue is gone. I now stay in the low 40's even with a full server of 28. So, if i may ask. Are you running a wireless connection?

---

### Post by lithiumKid1976 on 2013-11-06
hi 

thanks for the reply.
no, the pc itself is wired. 
broadband itself is a line of site connection, to a router, fed into the switch... (home network with 10 ports or so.)

using facebook etc, the connection is grand, installing software via ububtu is fine. it just seems to have major issues downloading TF2... the downloading info on steam, will show a block of data being downloaded, then it stops, then another block, then it stops....etc etc

on my windows machine i play MW , pings in 40-80. if i download it on windows, it would just be a constant download, it could get slow at times, but it would never drop, not really sure why its happening to my ubuntu machine..

---

### Post by dannyboy79 on 2013-11-06
do you have an issue downloading any other large games? did this start happening when you moved your steam game storage location to the other hard drive?

---

### Post by lithiumKid1976 on 2013-11-06
hi dannyboy79

re "do you have an issue downloading any other large games? did this start happening when you moved your steam game storage location to the other hard drive? "

this i dont know, but will check to night... :)

---

### Post by efflandt on 2013-11-08
What is your broadband download speed (have you tested it on speedtest.net, not sure what country you are in or if that is international)? And how are you resuming the download? All you should have to do is start steam and any downloads should resume (without having to do anything else). And what file system are you storing it to on the other hard drive (is it a Linux file system with write permission for you)?

I think the TF2 download is over 6 GB and expands to about 12.5 GB when installed. My Team Fortress 2 directory is currently 18.5 GB probably due to content for specific servers.

---

### Post by lithiumKid1976 on 2013-11-08
thanks for all the replys,
in the end i had to run this again..(from steam support)
******************
1. Open Terminal

2. Type steam --reset

3. You will see the following:

Installing bootstrap /home/[username]/.steam/steam/bootstrap.tar.xz

Reset complete!
************
once i re-ran that, i re-downloaded steam client.
then the TF2 download started downloading in a steady, (if quite slow :) ) proceess.
steam now remembers how much of the download has been downloaded. so i can now complete the download over a few days.

(i live in rural ireland, no such thing as high speed broadband! :(  )

thanks everyone for your help / suggestions...

---

### Post by dannyboy79 on 2013-11-27
WOW, you weren't kidding. It's downloading at around 1.6KB/s. it's a 13BG game, this will take forever!  it finally finished up sometime last night. it was bouncing from around 2KB/s to 400KB/s and that's on a 30Mbps download line

---

### Post by lithiumKid1976 on 2013-11-28
> **dannyboy79 said:**
> WOW, you were kidding. It's downloading at around 1.6KB/s. it's a 13BG game, this will take forever!

sadly, its true :)

ive had serious grief in downloading this game. 


i had downloaded 5.5GB of it. there was light at the end of the tunnel.......and then, it reset it self to 0% and the download started again..... :mad:

so i decided id update to 13.10, and give ubuntu enough space to allow me to download TF2, without having to move the steam folder, to see if that will sort this issue.

Ill kick off the download tonight, should be ready for christmas day! :)
wish me luck!

---

### Post by oldrocker99 on 2013-11-28
When I download from Steam, the bitrate varies greatly for many downloads. A big game like Painkiller took at least a couple or five hours, but it did download. I haven't had too many complaints about Steam myself; it has allowed me to purchase some terrific games in the past year since I started running the beta, and it seemed that all the available games had already been released in various Humble Bundle; it's come a long way in the past year, and it appears that it will only get better.

A LOT better.

---

