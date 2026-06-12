---
title: "Planeshift install"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by music_man on 2006-07-15
Hi

I am trying to get planeshift and I cant seem to download it.

I go to the downloads page and am fronted with: PlaneShift_CBV0.3.015.i686.bin 

Which appears to be a really small file that doesn't run.

Any ideas on how I can download it please?

---

### Post by RavenOfOdin on 2006-07-15
1) Are you trying to download the Linux client?
2) Did you use BitTorrent? 
3) Did you chmod PlaneShift_CBV0.3.015.i686.bin with the +x flag?

I know there was a major version update a while ago which may result in some connection problems after this is resolved.

---

### Post by music_man on 2006-07-15
... no

So I should download the .torrent file and open it with some sort of program. 

Alternatively I could download that .bin file and do that flag thing...

I am an ex-Windows user and still figuring out how all this works. What is a .bin file?

---

### Post by RavenOfOdin on 2006-07-15
> **music_man said:**
> ... no

So I should download the .torrent file and open it with some sort of program. 

Alternatively I could download that .bin file and do that flag thing...

I am an ex-Windows user and still figuring out how all this works. What is a .bin file?

.bin == Binary file.

Its basically the main type of program in Linux, like an .exe.

BitTorrent is shipped with GNOME, and for KDE there is kTorrent.  Both are available in the repositories and there are many more on the Web proper. . .look for whichever BT software you want to use.

the chmod command will basically alter your permissions on that file to read, write, or execute.  Try this in a terminal:

```

cd /directory/you/saved/the/file/in
chmod 755 PlaneShift_CBV0.3.015.i686.bin

```

and then try executing the file again.

Or better yet you can right click on the file, select Properties, go to the "Permissions" tab and then select "Is executable."

---

### Post by music_man on 2006-07-15
Thanks

Do you know the command to get the default torrent one?

I chmodded it and it still wouldn't run. It says the download is 250Mb and the download I have is in the bytes...

---

### Post by RavenOfOdin on 2006-07-15
Then you'll need to download it using BitTorrent.

right clicking on its link should bring up "Open with BitTorrent."
BT is in the GNOME menu under Applications > Internet.

If that fails, redownload the file from the HTTP mirrors listed on the download page.

---

### Post by music_man on 2006-07-15
Bittorrent isn't there so I used gnome-btdownload and it said bad info. What HTTP mirrors? There are only those .bin files there and I can't get those going.

---

### Post by RavenOfOdin on 2006-07-15
I thought there were http mirrors available on the download page.

It may have changed since then - what with the regular PS developers not uploading to the mirror sites - and I'm not in the best position to check it out at the moment.

Try [http://forums.hydlaa.com](http://forums.hydlaa.com), and leave a question about getting it over there.  I'm sure they know where you can find it.

---

### Post by music_man on 2006-07-15
I found a working download site and it is downloading now. Thanks for your help!

---

### Post by merlyn on 2006-07-16
> **music_man said:**
> Hi

I am trying to get planeshift and I cant seem to download it.

I go to the downloads page and am fronted with: PlaneShift_CBV0.3.015.i686.bin 

Which appears to be a really small file that doesn't run.

Any ideas on how I can download it please?

Go to [this link]("http://hydlaa.com/smf/index.php?topic=19389.0") and download it from there.

This is as close to an 'official' release until it becomes avaiable for download via the Planeshift home page.

The binary provided has been compiled, if that is the correct term, (I'm not a programer), by a bloke known as Xordan. Xordan is the main Linux developer/maintainer for Planeshift, (to the best of my knowledge.

Once youv'e downloaded the binary you'll need to make it executable by doing the following in a terminal.

<code> chmod +x (filename) </code>

Once this is done, you can run the file by using the following command

<code> ./ (filename) </code>

This will launch a nice graphical installer, (bitrock). Follow the prompts and you'll be playing Planeshift in no time at all.

Did it myself just this afternoon.

Cheers.

P.S. If any of you out there know how to configure a post so that the 'code' appears in that nice little box, I'd appreciate a hint on how to do it. ;)

---

### Post by merlyn on 2006-07-16
> **merlyn said:**
> Go to [this link]("http://hydlaa.com/smf/index.php?topic=19389.0") and download it from there.

This is as close to an 'official' release until it becomes avaiable for download via the Planeshift home page.

The binary provided has been compiled, if that is the correct term, (I'm not a programer), by a bloke known as Xordan. Xordan is the main Linux developer/maintainer for Planeshift, (to the best of my knowledge.

Once youv'e downloaded the binary you'll need to make it executable by doing the following in a terminal.

<code> chmod +x (filename) </code>

Once this is done, you can run the file by using the following command

<code> ./ (filename) </code>

This will launch a nice graphical installer, (bitrock). Follow the prompts and you'll be playing Planeshift in no time at all.

Did it myself just this afternoon.

Cheers.

P.S. If any of you out there know how to configure a post so that the 'code' appears in that nice little box, I'd appreciate a hint on how to do it. ;)

Edit: P.P.S What on earth is going on with this forum! All I get is text basically on a white background. The end result is a jumble of posts with no clearly defined 'boundry' between posts. (screenshot attached).

---

### Post by patrick295767 on 2006-07-16
> **music_man said:**
> Hi

I am trying to get planeshift and I cant seem to download it.

I go to the downloads page and am fronted with: PlaneShift_CBV0.3.015.i686.bin 

Which appears to be a really small file that doesn't run.

Any ideas on how I can download it please?

Pitty I just deleted yesterday from my harddisk ... 
I needed space.
  
So, to install it, you would just need to download it from the http.
You unpack the archive if I recall well.
  
I installed it in /opt 
and runned it via : 
./pss 
or 
./psclient
 
I dont recall exactly.
This game is normally  easy to install.
  
(I'll install it again if I have some time, one day ... I wanna check if worlds are bigger) 
  
Nice game but I wasnt soo happy of the sight vue.

Very good game !


Cheers

---

### Post by music_man on 2006-07-16
I managed to download and run it thanks :).

It went too slow on my computer so I deleted it. mmm 350Mb of our bandwidth gone.

---

### Post by merlyn on 2006-07-16
> **music_man said:**
> I managed to download and run it thanks :).

It went too slow on my computer so I deleted it. mmm 350Mb of our bandwidth gone.

Sorry to hear that. :(

Given some of improvements listed in the [changelog]("http://www.planeshift.it/update0.3.015.html") for the current release, work was done to optimise the games networking.

The game is still in an early developmental stage, perhaps further improvement can be achieved in this area, and you'll be able to run it in then.

Cheers.

---

### Post by el mariachi on 2007-04-09
I installed it awhile back and now I want to install again but I can't sh the bin file, it just blinks the terminal (the rectangle, i dunno what his name lol) i did chmod +x

---

