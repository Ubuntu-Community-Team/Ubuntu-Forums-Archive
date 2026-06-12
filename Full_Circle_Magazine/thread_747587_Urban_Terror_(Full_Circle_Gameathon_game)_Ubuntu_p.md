---
title: "Urban Terror (Full Circle Gameathon game) Ubuntu package"
date: 2008-04-06
forum: Full Circle Magazine
---

### Post by onlineapps on 2008-04-06
Hey all,
For those excited about the Full Circle Gameathon but who are rather upset because they can't find a .deb package for their Ubuntu machine, I've created a .deb package. Also, stay tuned for the next issue of FCM when I explain how to create a .deb.

These have been updated for use with Jack Coulter's .deb.

[SIZE="4"][COLOR="DarkRed"]Install Instructions[/COLOR][/SIZE]

Put
```
deb http://ppa.launchpad.net/jscinoz/ubuntu hardy main
deb-src http://ppa.launchpad.net/jscinoz/ubuntu hardy main
```

In /etc/apt/sources.list

Run sudo apt-get update

Search for urbanterror and optionally urbanterror-server in Synaptic or Adept and install them.

Happy fragging!

---

### Post by scragar on 2008-04-06
any help getting a 64 bit deb anywhere?

---

### Post by onlineapps on 2008-04-06
Yeah, sorry about that. I'm not on a 64-bit machine, so I could test it or anything. If someone wants to donate a machine, I'll gladly put together one :)

I basically stripped out all the 64-bit, .exe, and .app pieces. Then, I created it with dpkg -b (I'll have a tutorial on that in Issue 12).

---

### Post by scragar on 2008-04-06
if you wanna email it to me I'll test it, getting ready to do a fresh install soon anyway(gonna upgrade to hardy via a clean install, make sure I've nothing I don't need).

email = my username @gmail.com

---

### Post by onlineapps on 2008-04-07
I sent you a link to the package. Let me know how it works.

---

### Post by ronniet on 2008-04-07
<shameless plug>

> **onlineapps said:**
> ...stay tuned for the next issue of FCM when I explain how to create a .deb

</shameless plug>

;) :D

---

### Post by scragar on 2008-04-07
with the 64 bit version I get told:
```
Failed to execute child process "/usr/share/UrbanTerror/ioUrbanTerror.x86_64" (Permission denied)
```

and after chmoding the entire folder the game starts to launch, then crashes(dumping me to a 640px wide image of the top left on my desktop with some strange colour filter and everything frozen. Waited 5 minutes, and nothing changed. This could be because I'm not using my proper graphics card drivers though -- uninstalled envy ones after they kept messing with movie players after every second restart, got annoying).

---

### Post by onlineapps on 2008-04-08
OK, I uploaded a new amd64 package.

---

### Post by scragar on 2008-04-08
New package worked perfectly on hardy 64, not tested on gutsy 64(would have to reboot for that), but I can't imagine any problems.

Thanks.

---

### Post by onlineapps on 2008-04-08
Terrific! I updated the post.

---

### Post by celsdogg on 2008-04-13
sweet man! thanks a lot for this! i was using it with the q3 engine, and was never able to solve the q3a no sound issue!

---

### Post by MaindotC on 2008-05-05
It seems the debian package is no longer being hosted on filefront.  Can anyone send it to me?  Thanks!

---

### Post by onlineapps on 2008-05-06
FileFront apparently didn't like it. Uploaded again.

---

### Post by MaindotC on 2008-05-06
Thank you :) I actually couldn't wait so I downloaded and installed my own way - placing the folder in /usr/local/games and putting my own entry in the menu.  Thank you anyway :)  Star for you!

---

### Post by jscinoz on 2008-05-07
I've got standards-compliant, complete debs for urbanterror, urbanterror-server, and urbanterror-data for all architectures on my PPA:

```
deb http://ppa.launchpad.net/jscinoz/ubuntu hardy main
deb-src http://ppa.launchpad.net/jscinoz/ubuntu hardy main
```

Use these and you can install/update UrbanTerror thorugh synaptic or any other apt frontend.

I am also in the process of getting this game included into Debian Unstable, if i am successful in getting it into Debian before the Import freeze, it will also be in Ubuntu 8.10.


Regards,
Jack Coulter

---

### Post by MaindotC on 2008-05-09
I can't find the file on file front doing a search for "urban terror" but I followed your link and downloaded the .deb.

jscinoz - When I add your repo I get the message:

```

The following packages have unmet dependencies:
  urbanterror-data: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages

```

I'm using gutsy per my sig - can you help me resolve this?  Thanks!

---

### Post by onlineapps on 2008-05-09
Odd... it installed fine for me. I would recommend using Jack Coulter's package above.

---

### Post by MaindotC on 2008-05-09
I just used the deb from filefront.  Unfortunately it keeps on freezing whenever I try to download a new list of games.$%()*!@

---

### Post by onlineapps on 2008-05-09
I *think* that's just an Urban Terror bug, not a .deb bug. Try the other package by Jack.

---

### Post by MaindotC on 2008-05-09
Well it was fine until I came up with the genius idea to add the 24-16 kernel to the 22-14 kernel that comes with Gutsy.  Even though I boot into the 22-14 kernel it seems like I've still f'd my system.

---

### Post by MaindotC on 2008-05-10
Just FYI - I removed the 24-16 kernel and I'm good with UT now.  The 24-16 still shows in /lib/modules and it's about a gig of files so it's definitely THE kernel but I followed the directions to remove it so whatever.  At least now it works.  Thanks again for posting that deb.

---

### Post by linuxlizard on 2008-05-14
Another thank you for the deb. Made installation a snap!

unfortunately I've got some sound problems with this deb. Sound is crackling. Anyone have a fix?

Thanks!

---

### Post by onlineapps on 2008-05-14
Odd. Did you try the original (non-deb) version? If not, try Jack's

---

### Post by linuxlizard on 2008-05-14
ah, I was trying the original version.

So I did a complete uninstall, and tried Jacks.

I *think* it sounds better now, but I can't be sure because I'm now not able to retrieve the master server list...:(

---

### Post by MaindotC on 2008-06-17
I had to reinstall.  Does anyone have the deb that I could have?  Can you upload it to getdeb.net instead of filefront?  Thanks!

---

### Post by onlineapps on 2008-06-17
I can upload it again, but you're much better off with Jack's.

---

### Post by jsully1 on 2008-06-17
Just wanted to chime in and express my thanks for your repo.  Worked great!

---

### Post by MaindotC on 2008-06-17
I added the repo and downloaded.  Thank you very much!  Unfortunately I set the texture detail to "High" (just testing to see if my lapper could handle it) and it became choppy and every other setting results in the same thing.  It seems that this setting puts some type of permanent setting somewhere :(  I'll try and figure it out.

Edit: Restarted UT and it went back to smooth operation.  Strange - I thought when you change the texture detail settings it restarts UT anyway.

---

### Post by altonbr on 2008-06-22
[http://files.filefront.com/ioUrbanTerror+14+i386deb/;10143053;/fileinfo.html](http://files.filefront.com/ioUrbanTerror+14+i386deb/;10143053;/fileinfo.html) redirects to [http://www.filefront.com/](http://www.filefront.com/). Maybe you should take down that link? I know you stated it is not defunct, but still...

How's this game looking for inclusion in Debian/Ubuntu 8.10?

---

### Post by onlineapps on 2008-06-22
Dang Filefront. I guess they didn't like my .deb.

---

### Post by Lusse on 2008-08-07
The repository worked excelent for me thanks! =D>

The mouse pointer is still visible and always stuck in the middle which is cind of annoying so plz if anyone know how to fix it!

---

### Post by aenesias on 2008-11-08
> **jscinoz said:**
> I've got standards-compliant, complete debs for urbanterror, urbanterror-server, and urbanterror-data for all architectures on my PPA:

```
deb http://ppa.launchpad.net/jscinoz/ubuntu hardy main
deb-src http://ppa.launchpad.net/jscinoz/ubuntu hardy main
```

Use these and you can install/update UrbanTerror thorugh synaptic or any other apt frontend.

I am also in the process of getting this game included into Debian Unstable, if i am successful in getting it into Debian before the Import freeze, it will also be in Ubuntu 8.10.


Regards,
Jack Coulter

I wonder if the package is ready for intrepid ??
Thanks for your efforts ..

---

### Post by Interpreter on 2008-11-09
+1

---

### Post by altonbr on 2008-11-09
> **aenesias said:**
> I wonder if the package is ready for intrepid ??
Thanks for your efforts ..

This is his PPA: [https://launchpad.net/~jscinoz/+archive](https://launchpad.net/~jscinoz/+archive) and it doesn't look like he's compiled it for Intrepid yet.

---

### Post by aenesias on 2008-11-09
> **altonbr said:**
> This is his PPA: [https://launchpad.net/~jscinoz/+archive](https://launchpad.net/~jscinoz/+archive) and it doesn't look like he's compiled it for Intrepid yet.

Thanks 

I am afraid to install the one for hardy ...

Has anybody installed it to intrepid is it works on intrepid?

---

### Post by littletinman on 2008-11-11
Hey, Phil R. who wrote the review here. for intrepid it works awesome in 32 bit, and in 64 bit i run it under wine. It works perfectly under wine which is great, because i can also minimize it to my desktop while the maps are switching, and then bring it back up when the game starts.

---

### Post by aenesias on 2008-11-11
> **littletinman said:**
> Hey, Phil R. who wrote the review here. for intrepid it works awesome in 32 bit, and in 64 bit i run it under wine. It works perfectly under wine which is great, because i can also minimize it to my desktop while the maps are switching, and then bring it back up when the game starts.

i ll try it thanks

---

### Post by garyedwardjohnston on 2008-11-19
> **aenesias said:**
> i wonder if the package is ready for intrepid ??
Thanks for your efforts ..

+1

---

### Post by dannytatom on 2008-12-24
> **aenesias said:**
> Thanks 

I am afraid to install the one for hardy ...

Has anybody installed it to intrepid is it works on intrepid?

I'm wondering this too, I can't find a deb for intrepid. ;o

---

### Post by thechitowncubs on 2009-02-25
also wondering about intrepid!

---

### Post by Orlsend on 2009-02-27
I though that the cool thing about UT4 is you dont have to compile or install it. Its ready to go as soon you run the script.

---

### Post by MortenGungle on 2009-07-27
Just like to add that the repository below works on Jaunty...  Thanks Jack.

deb [http://ppa.launchpad.net/jscinoz/ubuntu](http://ppa.launchpad.net/jscinoz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/jscinoz/ubuntu](http://ppa.launchpad.net/jscinoz/ubuntu) hardy main

---

### Post by xiaoqi on 2009-08-02
Using 9.04, had added the two lines' source, but when "sudo apt-get update",
got below error message:

======
......
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources [1391B]                                       
Fetched 29.0kB in 7s (4139B/s)                                                                  
W: Failed to fetch [http://ppa.launchpad/net/jscinoz/ubuntu/dists/hardy/main/binary-i386/Packages](http://ppa.launchpad/net/jscinoz/ubuntu/dists/hardy/main/binary-i386/Packages)  404 /net/jscinoz/ubuntu/dists/hardy/main/binary-i386/Packages&

E: Some index files failed to download, they have been ignored, or old ones used instead.
======

What's that mean? Thanks.

---

### Post by CRAY-4 on 2009-10-11
also there's playdeb [http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)

---

### Post by faralai on 2011-01-14
i used the repository to install the server of urban terror

where the config file is?

---

### Post by slavinzing56 on 2011-08-08
sweet man! thanks a lot for this! i was using it with the q3 engine, and was never able to solve the q3a no sound issue!

---

### Post by Sef on 2011-08-09
Necromancing. Time for this thread to permanently rest in peace.

---

