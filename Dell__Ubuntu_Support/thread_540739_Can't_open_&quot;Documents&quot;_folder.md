---
title: "Can't open &quot;Documents&quot; folder"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by sheldon1 on 2007-09-01
Hi,

I recently created a copy of my "Documents" folder so that I could put it onto my panel. I made a copy of the destktop version and dragged it onto the panel. Since then I have not been able to open either folder, or access any of the files that were (are?) in that folder. I get an error message:

Could not show 'file:///home/sheldon/Desktop/Documents
The location or file could not be found.

I've tried to access the folder and the files in it in all sorts of ways, but I can't open it. I have many hours of work in that folder that I would like to have back. Can anybody help?

---

### Post by aysiu on 2007-09-01
Can you open a [terminal](http://www.psychocats.net/ubuntu/terminal), paste in these commands, and then copy and paste the output back here? ```
cd /home/sheldon/Desktop
ls -al
```

---

### Post by sheldon1 on 2007-09-02
sheldon@dell:~$ cd /home/sheldon/Desktop
sheldon@dell:~/Desktop$ ls -al
total 34
drwxr-xr-x   2 sheldon sheldon  1024 2007-09-01 21:40 .
drwxr-xr-x 159 sheldon sheldon  5120 2007-09-02 13:43 ..
-rw-r--r--   1 sheldon sheldon  7613 2007-07-25 15:03 Card Cutting Template.ott
-rw-r--r--   1 sheldon sheldon   290 2007-08-24 14:12 Documents-1.desktop
-rw-r--r--   1 sheldon sheldon 17654 2007-09-01 21:40 Download Document.html
sheldon@dell:~/Desktop$

---

### Post by Afishionado on 2007-09-02
My guess is that it's just a messed-up shortcut. It seems to be looking for a shortcut named "Documents" that's been renamed "Documents-1".

Can you still get at your documents by going to your "Places" menu at the top of the screen and selecting Documents there?

---

### Post by aysiu on 2007-09-02
All the items in your Desktop folder are files (.ott, .desktop, .html). None is a folder. There is no *Documents* folder.

---

### Post by gbrainin on 2007-09-02
It sounds like the folder got moved somehow, and the link is now pointing to where it used to be.  I would suggest trying to locate the missing folder by searching for something you know is in it.  You can use the find command to locate it, and that'll tell you where the directory is.

For example, if you know the folder has a file in it named "Myfile.doc," you open a terminal window and run the command:

```
cd
find . -iname Myfile.doc -print
```

This will search your home directory and all subdirectories for a file with that name, and print any matches it finds.  This should help you locate your missing folder, assuming it's still somewhere in your home directory.  Note that if your filename has any spaces in it, the command becomes tricky, so try to use a filename without spaces.

---

### Post by sheldon1 on 2007-09-02
I cannot access the *Documents* file anywhere, and I can't open any of the files that used to be in it. Thanks for the help anyways.

I tried using the regular search program in Places, but couldn't find any of the documents I know used to be there. There are documents that were in the Documents file in my Recent Documents, but they won't open, either.

I'll have access to a printer tomorrow to key in that code, gbrainin.

Any other ideas?

---

### Post by Afishionado on 2007-09-03
Post the output from:

ls -la /home/sheldon

---

### Post by sheldon1 on 2007-09-04
sheldon@dell:~$ ls -la /home/sheldon
total 1871701
drwxr-xr-x 161 sheldon sheldon       5120 2007-09-03 22:06 .
drwxr-xr-x   5 root    root          1024 2007-06-17 02:05 ..
-rw-r--r--   1 sheldon sheldon  729705222 2007-08-18 18:03 aemp_live_in_nyc.avi
-rw-r--r--   1 sheldon sheldon 1176011678 2007-08-19 13:31 aemp_live_in_nyc.zvm.avi
drwx------   3 sheldon sheldon       1024 2007-08-12 23:18 Andy Narell - Steel Drums
drwxr-xr-x   4 sheldon sheldon       1024 2007-08-22 17:22 .armagetronad
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 12:58 Audioslave
drwx------   3 sheldon sheldon       1024 2007-08-12 23:20 Bahia Black - Brasilian Modern Percussion
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-02 18:01 Barry White
-rw-------   1 sheldon sheldon        189 2007-09-03 22:10 .bash_history
-rw-r--r--   1 sheldon sheldon        220 2007-06-13 10:26 .bash_logout
-rw-r--r--   1 sheldon sheldon       2298 2007-06-13 10:26 .bashrc
drwx------   3 sheldon sheldon       1024 2007-08-12 23:35 Bebel Gilberto - Female Brasilian Jazz Samba
drwx------   3 sheldon sheldon       1024 2007-08-12 23:43 Billy Idol - 80s punk rock
drwxr-xr-x   2 sheldon sheldon       1024 2007-08-30 12:25 Biology
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-15 17:17 Bob Dylan
drwx------   3 sheldon sheldon       1024 2007-08-12 23:19 Boston - 70s Rock
drwx------   4 sheldon sheldon       1024 2007-08-12 23:54 Brasilian - Various Artists
drwx------   3 sheldon sheldon       1024 2007-08-12 23:42 Brazil - Bahian
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:19 Cannonball%20Adderley
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-15 15:04 Cannonball Adderley
drwxr-xr-x   2 sheldon sheldon       1024 2007-08-31 08:51 Chemistry
-rw-------   1 sheldon sheldon          0 2007-06-29 19:26 .civserver_history
drwxr-xr-x   4 sheldon sheldon       1024 2007-09-01 21:25 .clamtk
drwx------   3 sheldon sheldon       1024 2007-08-12 23:18 Collective Soul - 90s
drwx------   4 sheldon sheldon       1024 2007-06-28 12:50 .config
drwx------   3 sheldon sheldon       1024 2007-08-12 23:39 Counting Crows
drwxr-xr-x   4 sheldon sheldon       1024 2007-08-25 20:14 Cream
drwxr-xr-x   2 sheldon sheldon       1024 2007-09-01 21:40 Desktop
drwx------   3 sheldon sheldon       1024 2007-08-12 23:21 Dianna Krall - Contemporary Female Jazz
drwx------   3 sheldon sheldon       1024 2007-08-12 23:44 Dire Straits
-rw-------   1 sheldon sheldon         26 2007-06-13 10:26 .dmrc
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-19 16:58 Donald Byrd
drwx------   3 sheldon sheldon       1024 2007-08-12 23:45 Elton John - Classic
drwx------   2 sheldon games         1024 2007-06-17 12:06 .emilia
-rw-------   1 sheldon sheldon         16 2007-06-13 10:26 .esd_auth
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-02 13:56 Everclear
drwxr-xr-x   8 sheldon sheldon       1024 2007-09-03 15:54 .evolution
lrwxrwxrwx   1 sheldon sheldon         26 2007-06-13 10:26 Examples -> /usr/share/example-content
-rw-r--r--   1 sheldon sheldon       1198 2007-07-09 12:13 .fbrc
-rw-r--r--   1 sheldon sheldon      22713 2007-08-14 16:39 federal loan rights.odt
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-04 19:24 .fontconfig
drwx------   3 sheldon sheldon       1024 2007-08-12 23:22 Fourplay - Contemporary Jazz
drwxr-xr-x   2 sheldon sheldon       1024 2007-06-29 19:25 .freeciv
drwx------   4 sheldon sheldon       1024 2007-09-01 23:13 .gaim
drwx------   5 sheldon sheldon       1024 2007-09-03 22:06 .gconf
drwx------   2 sheldon sheldon       1024 2007-09-03 22:09 .gconfd
drwxr-xr-x  21 sheldon sheldon       1024 2007-07-04 20:01 .gimp-2.2
-rw-r-----   1 sheldon sheldon          0 2007-09-02 14:11 .gksu.lock
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-21 22:04 .glchess
-rw-r--r--   1 sheldon sheldon        357 2007-09-03 15:53 .gnomad2rc
drwxr-xr-x   4 sheldon sheldon       1024 2007-06-15 13:25 .gnome
drwx------  20 sheldon sheldon       1024 2007-09-03 15:54 .gnome2
drwx------   2 sheldon sheldon       1024 2007-06-13 10:26 .gnome2_private
drwxr-xr-x   6 sheldon sheldon       1024 2007-07-31 17:44 Gorillaz
drwxr-xr-x   2 sheldon sheldon       1024 2007-09-01 21:03 .gpilotd
-rw-r--r--   1 sheldon sheldon          5 2007-09-03 15:49 .gpilotd.pid
drwxr-xr-x   2 sheldon sheldon       1024 2007-08-07 09:01 .gstreamer-0.10
-rw-r--r--   1 sheldon sheldon        400 2007-07-28 00:13 .gtickrc
drwxr-xr-x   2 sheldon sheldon       1024 2007-09-03 15:51 .gtimelog
-rw-------   1 sheldon sheldon         65 2007-07-31 17:18 .gtk-bookmarks
drwxr-xr-x   2 sheldon sheldon       1024 2007-06-16 21:34 .gtkpod
-rw-r--r--   1 sheldon sheldon         89 2007-06-13 10:26 .gtkrc-1.2-gnome2
-rw-r--r--   1 sheldon sheldon        727 2007-08-06 21:37 .gtk-recordmydesktop
drwx------   2 sheldon sheldon       1024 2007-07-07 12:23 .gxine
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Hans%20Zimmer
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-17 17:26 Hans Zimmer
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Howard%20Shore
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-17 17:33 Howard Shore
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-20 12:19 .hydrogen
-rw-------   1 sheldon sheldon       3665 2007-09-03 22:06 .ICEauthority
drwxr-xr-x   2 sheldon sheldon       1024 2007-06-13 10:32 .icons
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Immortal%20Technique
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-15 14:54 Immortal Technique
-rw-r--r--   1 sheldon sheldon         92 2007-07-31 18:09 .iriverter.conf
-rw-r--r--   1 sheldon sheldon       5974 2007-08-19 13:31 .iriverter.log
drwx------   3 sheldon sheldon       1024 2007-08-12 23:37 Israel Kamakawiwo'ole - Classic Hawaiian
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-20 12:28 .jackbeat
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-20 12:29 .jamin
drwxr-xr-x   4 sheldon sheldon       1024 2007-06-28 12:48 .java
drwx------   3 sheldon sheldon       1024 2007-08-12 23:24 Jean-Luc Ponty - Contemporary Jazz Violinist
drwxr-xr-x   4 sheldon sheldon       1024 2007-07-31 17:44 Jimi%20Hendrix
drwxr-xr-x   4 sheldon sheldon       1024 2007-07-20 17:07 Jimi Hendrix
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 John%20Lennon
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 John%20Mayer
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-17 17:09 John Lennon
drwxr-xr-x   5 sheldon sheldon       1024 2007-09-02 13:58 John Mayer
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-02 14:00 Journey
drwxr-xr-x   5 sheldon sheldon       1024 2007-07-31 17:44 Kansas
drwx------   4 sheldon sheldon       1024 2007-08-12 23:18 Kansas - 70s Rock
drwx------   3 sheldon sheldon       1024 2007-07-31 12:52 .kde
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-07 14:53 .lastfm
drwx------   3 sheldon sheldon       1024 2007-08-12 23:25 Led Zeppelin - Classic Rock
drwx------   4 sheldon games         1024 2007-07-07 15:02 .lgames
drwx------   2 sheldon sheldon       1024 2007-06-17 02:38 .lincity
drwx------   3 sheldon sheldon       1024 2007-08-12 23:26 Lyle Mays - Contemporary Jazz Pianist
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-02 14:13 Lynyrd Skynyrd
drwx------   3 sheldon sheldon       1024 2007-06-15 08:19 .macromedia
drwxr-xr-x   2 sheldon sheldon       1024 2007-06-28 11:41 MAPS
drwxr-xr-x   2 sheldon sheldon       1024 2007-09-02 21:00 Math 170
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-15 00:33 .mcop
-rw-------   1 sheldon sheldon         31 2007-08-09 22:06 .mcoprc
drwx------   3 sheldon sheldon       1024 2007-06-13 10:26 .metacity
drwx------   3 sheldon sheldon       1024 2007-08-12 23:12 Michael Cundick - My 2nd Cousin - Hard rock violin
drwxr-xr-x   4 sheldon sheldon       1024 2007-08-19 17:14 Miles Davis
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Mixed%20by%20Dan
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-27 15:15 Mixed by Dan
drwx------   3 sheldon sheldon       1024 2007-06-13 10:55 .mozilla
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-20 12:51 .mplayer
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-20 12:42 Music
drwx------   3 sheldon sheldon       1024 2007-08-12 23:47 Nando Lauria - Brazil Guitar
drwxr-xr-x   3 sheldon sheldon       4096 2007-09-03 15:54 .nautilus
-rw-r--r--   1 sheldon sheldon     175917 2007-08-11 21:22 nautilus-debug-log.txt
drwx------   3 sheldon sheldon       1024 2007-08-12 23:46 Nestor Torres - Latin Jazz Flute
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-30 18:27 .neverball
-rw-r--r--   1 sheldon sheldon      49389 2007-09-01 21:35 not just about oil.odt
drwx------   3 sheldon sheldon       1024 2007-09-02 21:01 .openoffice.org2
dr-x------   3 sheldon sheldon       1024 2007-08-12 23:48 Oscar Peterson Classic Jazz Trio
drwx------   3 sheldon sheldon       1024 2007-08-12 23:29 Oystein Sevag - new age (from norway)
drwxr-xr-x   4 sheldon sheldon       1024 2007-07-31 17:44 Oysterhead
drwx------   3 sheldon sheldon       1024 2007-08-12 23:47 Ozzy Osbourne
drwx------   4 sheldon sheldon       1024 2007-08-12 23:27 Pat Metheny - My favorite fusion jazz guitarist
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Paul%20Simon
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-17 18:12 Paul Simon
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Peter%20Erskine
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-20 16:42 Peter Erskine
drwxr-xr-x   5 sheldon sheldon       1024 2007-07-31 17:44 Phish
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Pink%20Floyd
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-20 17:45 Pink Floyd
drwx------   3 sheldon sheldon       1024 2007-08-12 23:31 Pink Floyd - Drugs without Drugs 70s rock
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-30 18:30 .ppracer
drwxr-xr-x   7 sheldon sheldon       1024 2007-08-02 17:05 Primus
-rw-r--r--   1 sheldon sheldon        566 2007-06-13 10:26 .profile
-rw-r--r--   1 sheldon sheldon      37201 2007-08-06 20:15 Pro israel hawks and the second gulf war.odt
drwxr-xr-x   2 sheldon sheldon       1024 2007-09-01 21:27 .qt
drwx------   7 sheldon sheldon       1024 2007-09-02 14:07 Queen
drwx------   2 sheldon sheldon       1024 2007-08-12 23:14 Quiet Fire - New Age
drwx------   3 sheldon sheldon       1024 2007-08-12 23:49 Radio West Talk Show  - Doug Fabrizio
drwxr-xr-x   6 sheldon sheldon       1024 2007-07-31 17:44 Rage%20Against%20the%20Machine
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 Rage%20Against%20The%20Machine
drwxr-xr-x   6 sheldon sheldon       1024 2007-07-22 19:46 Rage Against the Machine
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-23 14:01 Rage Against The Machine
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-20 12:24 .rainbow-cache
drwx------   3 sheldon sheldon       1024 2007-08-12 23:32 Ramsey Lewis - Classic Piano Jazz
drwx------   3 sheldon sheldon       1024 2007-08-12 23:33 Ray Brown - Classic Jazz
-rw-------   1 sheldon sheldon      17564 2007-09-02 21:01 .recently-used
-rw-r--r--   1 sheldon sheldon      57780 2007-09-02 20:55 .recently-used.xbel
drwxr-xr-x   6 sheldon sheldon       1024 2007-07-31 17:44 Red%20Hot%20Chili%20Peppers
drwxr-xr-x   6 sheldon sheldon       1024 2007-07-31 17:35 Red Hot Chili Peppers
drwx------   3 sheldon sheldon       1024 2007-08-12 23:34 Robert Miles - New Age Dream Music
dr-x------   3 sheldon sheldon       1024 2007-08-12 23:49 Rosie Thomas - sweet Female new age mellow
-rw-------   1 sheldon sheldon     541313 2007-07-07 15:16 rudimentsequence2.pdf
-rw-------   1 sheldon sheldon     475367 2007-07-07 15:17 rudimentsequence3.pdf
-rw-------   1 sheldon sheldon     332764 2007-07-07 15:17 rudimentsequence4.pdf
drwx------   3 sheldon sheldon       1024 2007-08-12 23:51 Sade - Contemporary Female Jazz
drwxrwx---   3 sheldon sheldon       1024 2007-07-04 19:16 .sane
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-20 16:57 Santana
dr-x------   3 sheldon sheldon       1024 2007-08-12 23:50 Scorpions - Classic rock
drwxr-xr-x   3 sheldon sheldon       1024 2007-09-02 13:34 Seal
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-20 12:37 SSDP
drwx------   3 sheldon sheldon       1024 2007-08-12 23:19 Steely Dan - Jazz crossover
drwx------   3 sheldon sheldon       1024 2007-08-12 23:51 Sting
drwxr-xr-x   4 sheldon sheldon       1024 2007-07-31 17:44 Sublime
-rw-r--r--   1 sheldon sheldon          0 2007-06-13 10:31 .sudo_as_admin_successful
-rw-r--r--   1 sheldon sheldon      37302 2007-08-11 15:07 ten commandments for middeast peace.odt
drwxr-xr-x   7 sheldon sheldon       1024 2007-07-31 17:44 The%20Beatles
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-31 17:44 The%20Grateful%20Dead
drwxr-xr-x   7 sheldon sheldon       1024 2007-07-31 17:44 The%20Police
drwxr-xr-x   7 sheldon sheldon       1024 2007-07-07 15:43 The Beatles
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-17 12:10 The Grateful Dead
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-19 17:04 Thelonious Monk
drwxr-xr-x   2 sheldon sheldon       1024 2007-06-13 10:32 .themes
drwxr-x---   2 sheldon sheldon       1024 2007-09-01 19:11 The MondoGlobo Network
drwxr-xr-x   7 sheldon sheldon       1024 2007-07-07 12:31 The Police
drwxr-xr-x   4 sheldon sheldon       1024 2007-08-02 14:41 The Smashing Pumpkins
drwx------   3 sheldon sheldon       1024 2007-08-12 23:52 Thomas Dolby - Early 90s Punk
drwx------   5 sheldon sheldon       1024 2007-07-20 19:34 .thumbnails
drwxr-xr-x   3 sheldon sheldon       1024 2007-08-29 13:05 .tomboy
-rw-r--r--   1 sheldon sheldon       1268 2007-08-29 13:05 .tomboy.log
drwxr-xr-x   2 sheldon sheldon       1024 2007-08-22 21:04 Toothpaste For Dinner
drwx------   5 sheldon sheldon       1024 2007-08-30 08:50 .Trash
drwx------   2 sheldon sheldon       1024 2007-06-13 11:09 .tsclient
-rw-r--r--   1 sheldon sheldon    1440071 2007-07-29 21:09 tux_sshot_0.ppm
drwxr-xr-x   2 sheldon sheldon       1024 2007-08-29 12:28 Type name of new folder
drwxr-xr-x   2 sheldon sheldon       1024 2007-06-15 13:26 .update-manager-core
drwx------   2 sheldon sheldon       1024 2007-07-19 20:31 .update-notifier
drwxr-xr-x   3 sheldon sheldon       1024 2007-09-02 13:43 Van Halen
drwxr-xr-x   4 sheldon sheldon       1024 2007-07-31 17:44 Various%20Artists
drwxr-xr-x   6 sheldon sheldon       1024 2007-09-02 13:40 Various Artists
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-07 15:57 Vocab
drwxr-xr-x   2 sheldon sheldon       1024 2007-07-07 15:56 Vocabularies
drwxr-xr-x   2 sheldon sheldon       1024 2007-08-29 13:29 .wapi
drwxr-xr-x   3 sheldon sheldon       1024 2007-06-28 12:25 Weezer
-rw-------   1 sheldon sheldon        115 2007-09-03 22:06 .Xauthority
drwx------   3 sheldon sheldon       1024 2007-09-01 19:47 .xchat2
drwxr-xr-x   3 sheldon sheldon       1024 2007-07-07 12:23 .xine
drwx------   5 sheldon sheldon       1024 2007-06-18 19:35 .xmoto
-rw-r--r--   1 sheldon sheldon       4385 2007-09-03 22:08 .xsession-errors
sheldon@dell:~$ ________________

---

