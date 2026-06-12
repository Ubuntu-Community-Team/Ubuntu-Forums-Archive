---
title: "Headless torrent/samba server"
date: 2009-04-20
forum: General Help
---

### Post by Groovechild on 2009-04-20
Hey guys and gals,

I would like to construct a small box (Intel D945GCLF2) whose sole purpose is to play with torrents and share samba so I can browse internally. I am no linux guru by any means, but have no problems with ssh if I have some good docs. The distro I installed is Ubuntu 8.10 Server (x32). No gui on there, hoping I don't need one if I can manage the torrent server through the web or a windows client.

What I'd like to do is setup some type of torrent server that runs fulltime that I can access either from another machine either via a client program, or better yet, through the web. I think Azureus used to do this in the past, where you can access on one of the web ports and java, but now since they are Vuze not sure if that is still possible.

Once the torrents download, I would just browse the samba share and pull them down or stream them from the samba locations via media extender or the like.

Any recommendations out there? I imagine there is prolly a good amount of people out there doing this.

Thanks in advance as always,
Groovie

---

### Post by prem1er on 2009-04-20
Yes, I run a similar setup using rTorrent as my torrent client.  It runs through a screen so you can view it over the command line and if you have multiple user logging in they can all view the same client.  I have heard about issues with writing to a NTFS partition with older versions of rTorrent (I don't know if this makes a difference) but you might want to do some research on that first.  Let me know if you have any other questions about it.

---

### Post by aeiah on 2009-04-20
either rtorrent and set it to look in a folder for .torrent files to add, and you just drop them in there, or use deluge.

deluge can run as a daemon with the gui connecting to it. the gui doesnt need to be on the same server as the daemon that's doing the downloading. deluge also has a web app if you arent on a pc with the deluge gui on it. this way you can work with your torrents like you normally would locally, and when you've finished setting up priorities, deleting old ones blah blah blah you can disconnect (ie close) the gui and the daemon on your fileserver will just keep on running


edit: note that only the new versions of deluge have the daemon functionality. the older circa 0.5 versions are just like a normal torrent client. i dunno if your version of ubuntu has the new version but it's available as a .deb and in its own repo at the deluge website.

---

### Post by MN Noob on 2009-04-20
If I understand you correctly, I am using a type of setup that you want. I am using rtorrent and nfs. I am using this configuration for rtorrent [http://rtgui.googlecode.com/files/.rtorrent.rc]("http://rtgui.googlecode.com/files/.rtorrent.rc") Then I use nfs to export the auto folder and the completed folder. Then just drag and drop the torrent files into the auto folder and rtorrent should start downloading in a few seconds. It downloads the torrent to the downloading folder and once completed, moves it to the completed folder.

From there, I generally just ssh into the box and rsync the file to my Mac to watch. (NFS is too slow) Although, if I am lazy I just mount the completed folder and copy the file.

You can set rtorrent to run as a daemon, I didn't though. I just use screen and let it run in the background and close it when I am done. I saw a howto on getting it to run as a daemon, but can't find the link right now.

---

### Post by edthefox on 2009-04-20
I also have a similar setup at home. I also run a headless server and use rtorrent with screen and it makes a perfect setup for me. I don't run samba though.  Instead, I found it easier to run proftpd and access it via sftp. That way, I can get to it and transfer files anywhere I can open a ssh session from.  There's a slight learning curve using rtorrent but it works great after you get the hang of things.

On a side note, I also run squid so that I can route anything that might be blocked by the corporate filters and such here at work.

---

### Post by whitethorn on 2009-04-20
If you have ubuntu 8.10 installed then you're fine with rtorrent and nfs file systems.  The 8.10 kernel has a newer version of fuse (I believe that's what it's called) needed to write to nfs. 8.04 didn't work.

---

### Post by Groovechild on 2009-04-20
Thanks for the quick replies!

I did the apt-get install rtorrent which appears to work as expected (haven't messed with the config yet, but looks straightfoward).
Have you guys tried the client programs to access rtorrent remotely, like nTorrent or the like? Ideally I'd like to have a web front-end for rTorrent if possible just so that wifey can browse there from her laptop, drop a torrent, and then pickup the payload later. Methinks she will no likey ctrl-A or ctrl-S and the like.
I was thinking samba just so I can map two drives for her on her Windows machine, one samba share for dropping the torrent file, and another share for her to pick it up, and a web page (via desktop shortcut) for her to click on so she can get a feel for how long she has left on the downloads.

Sound doable?

I guess I should have labelled the title of the post to **Headless torrent/samba server for wifey**!

---

### Post by Groovechild on 2009-04-20
The deluge client actually looks really cool! Definitely digging the fact it was a web interface. 
How are people's experiences with deluge here?

---

### Post by theRick on 2009-04-20
I personally use torrent flux which includes a web interface. Combined with ddclient and a domain from dyndns this has been the perfect remote solution for me.

rTorrent might be better, I don't know, but torrentflux was a breeze.

---

### Post by cackles on 2009-04-24
Heres a tut I wrote, it will only work on 8.10 for now, theres either bugs or some mods stopping it from working on the latest version. Im working on updating it as we speak.

[http://ubuntuforums.org/showthread.php?t=799712](http://ubuntuforums.org/showthread.php?t=799712)

---

