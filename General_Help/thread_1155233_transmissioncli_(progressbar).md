---
title: "transmissioncli (progressbar?)"
date: 2009-05-10
forum: General Help
---

### Post by Miles_Prower on 2009-05-10
So, I've been messing with transmissioncli recently, and I've gotten this far:

```
[botnik@localhost torrent_files]$ transmissioncli &#3232;_&#3232;.torrent -p &#3232;_&#3232; -o ~/torrent_wasteland/
[2009/05/10 - 15:09:01] No owner supplied, using 'n/a'.
[2009/05/10 - 15:09:01] transmission 1.22 (6191) starting up :
[2009/05/10 - 15:09:01]  - torrent : &#3232;_&#3232;.torrent
[2009/05/10 - 15:09:01]  - owner : n/a
[2009/05/10 - 15:09:01]  - dieWhenDone : 0
[2009/05/10 - 15:09:01]  - seedLimit : 0
[2009/05/10 - 15:09:01]  - bindPort : &#3232;_&#3232;
[2009/05/10 - 15:09:01]  - uploadLimit : 20
[2009/05/10 - 15:09:01]  - downloadLimit : -1
[2009/05/10 - 15:09:01]  - natTraversal : 0
[2009/05/10 - 15:09:01]  - displayInterval : 0
[2009/05/10 - 15:09:01] Initialized status-facility. (&#3232;_&#3232;.torrent.stat)
[2009/05/10 - 15:09:01] Initialized command-facility. (&#3232;_&#3232;.torrent.cmd)
[2009/05/10 - 15:09:01] Wrote pid-file: &#3232;_&#3232;.torrent.pid (692)
[2009/05/10 - 15:09:01] Transmission up and running.

```

Files are being generated in the output folder, but I've got no clue as to the current progress of the download. Is there some way to get a progress bar, or do you just have to be patient? Also, I'd like to avoid having a terminal window and an ssh connection open for the duration of the torrent download, is there some way I can start the torrent, then disconnect ssh?

Thanks,
Tails

---

### Post by geirha on 2009-05-10
One option is to start it in screen. You ssh in, run "screen", then run transmissioncli. When you want to disconnect, hit Ctrl+A+D to detach from the screen, then log out from the ssh-session. The program will be running along in the background. You can later log back in and run "screen -r" to resume the screen.

A better option would be to use transmission-daemon. Transmission-daemon just runs in the background. You can then use the transmission-remote command to add/remove torrents, and check on their progress. You can also configure the transmission-daemon's web UI to allow connections from your other computer, then control transmission from your web browser. [http://trac.transmissionbt.com/wiki/HeadlessUsage](http://trac.transmissionbt.com/wiki/HeadlessUsage)

---

### Post by Miles_Prower on 2009-05-10
the screen command is awesome. thank you very much for that. I'll look into transmission-daemon, but I currently can't find a centos rpm for it.

//edit
Oh, right. I thought it was a standalone program for some reason... Anyways, thank you. I'll thumb through the man pages and see what's what.

---

### Post by Miles_Prower on 2009-05-11
tried desparately to hook up transmission-daemon, but can't even access it from localhost:9091. how hard would it be for someone with (very) little programming exp. to hack a progress bar into transmissioncli?

---

### Post by geirha on 2009-05-12
Not sure really. You could try asking in #transmission on irc.freenode.net, also, asking there about transmission-daemon will probably make it easier to set up, having live aid while you hack.

---

