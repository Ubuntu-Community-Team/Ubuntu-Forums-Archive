---
title: "googlearth"
date: 2009-02-08
forum: General Help
---

### Post by cowboy7305 on 2009-02-08
More than likely done to death but i cant fix it 
downloaded googleearth from the synaptic packages
and when i start to load it from applications internet i get these massages 
Could not create directory
/root/googleearth/cache
i then press ok 
and i get a notice saying 
google earth could not write to the current cach or myspace file location the values will be set as follows
my places path"/home/david/googleearth"
cach path "/home/david/googleearth/cache"
press ok 
then google earth starts up but it does notyhing no world in the veiw screen and i can do nothing with any thing and there does not look like any internet working with it 
iam using ubuntu 8.1 full install
many thanks if you can help me out 
i would have copied and pasted but i could not do it

---

### Post by taurus on 2009-02-08
Probably a permission problem.  From a terminal, run

```
sudo chown -R david:david /home/david/googleearth
ls -la ~/googleearth
```

---

### Post by cowboy7305 on 2009-02-08
Tried that 
got this message 
chown: cannot access `/home/david/googleearth': No such file or directory

---

### Post by taurus on 2009-02-08
Did you ever run GoogleEarth as root before (maybe using sudo)?  

What's the output of this command from a terminal?

```
ls -la ~
```

Did you press ok when it displayed that message?

> google earth could not write to the current cach or myspace file location the values will be set as follows
my places path"/home/david/googleearth"
cach path "/home/david/googleearth/cache"
press ok 

---

### Post by cowboy7305 on 2009-02-08
yes i pressed ok

---

### Post by cowboy7305 on 2009-02-08
Not as far as i know  from sudo 
i dont know much about that yet 
can i right into terminal and delete every thing that is on computer that has any thing to do with google earth and try loading it again

---

### Post by taurus on 2009-02-08
I don't know whether you have ~/googleearth or ~/.googleearth until you post the output of that command.

---

### Post by cowboy7305 on 2009-02-08
total 3140812
drwxr-xr-x 66 david david       4096 2009-02-08 15:02 .
drwxr-xr-x  3 root  root        4096 2009-01-31 09:43 ..
drwx------  3 david david       4096 2009-01-31 11:52 .adobe
drwxr-xr-x  4 david david       4096 2009-02-06 12:28 .aMule
drwxr-xr-x  2 david david       4096 2009-02-01 14:01 AUDIO_TS
-rw-r--r--  1 david david        396 2009-02-07 13:40 .balazar
drwxr-xr-x  3 david david       4096 2009-02-07 13:39 .balazar_saved_games
-rw-------  1 david david       3106 2009-02-08 16:57 .bash_history
-rw-r--r--  1 david david        220 2009-01-31 09:43 .bash_logout
-rw-r--r--  1 david david       3115 2009-01-31 09:43 .bashrc
drwx------  2 david david       4096 2009-02-02 21:59 .bogofilter
drwxr-xr-x  6 david david       4096 2009-02-03 20:51 .cache
drwxr-xr-x  4 david david       4096 2009-02-01 13:12 .clamtk
drwx------  3 david david       4096 2009-02-07 21:46 .compiz
drwxr-xr-x 11 david david       4096 2009-02-08 10:34 .config
drwx------  3 david david       4096 2009-01-31 10:09 .dbus
-rw-r--r--  1 david david         60 2009-02-03 20:41 .DCOPserver_david-desktop__0
lrwxrwxrwx  1 david david         40 2009-02-03 20:41 .DCOPserver_david-desktop_:0 -> /home/david/.DCOPserver_david-desktop__0
drwxr-xr-x  2 david david       4096 2009-02-08 09:16 Desktop
-rw-------  1 david david          2 2009-02-08 07:42 .dmrc
drwxr-xr-x  2 david david       4096 2009-01-31 10:09 Documents
drwxr-xr-x  8 david david       4096 2009-02-07 13:54 .dvdcss
drwxr-xr-x  2 david david       4096 2009-02-01 11:19 .dvdrip
drwxr-xr-x  4 david david       4096 2009-02-07 14:52 dvdrip-data
drwxr-xr-x  4 david david       4096 2009-02-01 11:19 .dvdrip-master
-rw-r--r--  1 david david      25771 2009-02-01 09:59 .dvdriprc
drwxr-xr-x  2 david david       4096 2009-02-05 05:56 dwhelper
-rw-------  1 david david         16 2009-01-31 10:09 .esd_auth
drwxr-xr-x  8 david david       4096 2009-02-04 20:36 .evolution
lrwxrwxrwx  1 david david         26 2009-01-31 09:43 Examples -> /usr/share/example-content
drwxr-xr-x  2 david david       4096 2009-02-08 08:04 .fontconfig
drwxr-xr-x  5 david david       4096 2009-02-01 09:39 FrostWire
drwxr-xr-x  6 david david       4096 2009-02-07 13:40 .frostwire4.17
drwx------  4 david david       4096 2009-02-08 07:42 .gconf
drwx------  2 david david       4096 2009-02-08 17:09 .gconfd
-rw-r-----  1 david david          0 2009-02-08 16:02 .gksu.lock
drwx------  3 david david       4096 2009-02-07 09:53 .gnome
drwx------ 13 david david       4096 2009-02-08 07:52 .gnome2
drwx------  2 david david       4096 2009-01-31 10:09 .gnome2_private
drwx------  2 david david       4096 2009-02-08 10:17 .gnupg
drwx------  6 david david       4096 2009-02-08 16:07 .googleearth
drwxr-xr-x  2 david david       4096 2009-02-05 21:54 .gstreamer-0.10
-rw-r--r--  1 david david        108 2009-02-08 08:56 .gtk-bookmarks
dr-x------  2 david david          0 2009-02-08 07:42 .gvfs
-rw-------  1 david david       2971 2009-02-08 07:42 .ICEauthority
drwxr-xr-x  2 david david       4096 2009-02-08 07:52 .icons
drwx------  3 david david       4096 2009-02-01 08:56 .kde
drwx------  5 david david       4096 2009-02-08 17:08 .licq
drwx------  3 david david       4096 2009-01-31 10:09 .local
drwx------  3 david david       4096 2009-02-07 09:53 .loki
drwx------  3 david david       4096 2009-01-31 11:52 .macromedia
drwxr-xr-x  3 david david       4096 2009-02-01 08:56 .mcop
-rw-------  1 david david         31 2009-02-03 05:59 .mcoprc
-rw-r--r--  1 david david 3212288000 2009-02-01 21:49 min.iso
drwx------  4 david david       4096 2009-02-04 20:39 .mozilla
drwx------  3 david david       4096 2009-02-04 20:39 .mozilla-thunderbird
drwxr-xr-x  2 david david       4096 2009-02-08 08:10 .mplayer
drwxr-xr-x  2 david david       4096 2009-02-07 06:18 Music
drwxr-xr-x  2 david david       4096 2009-02-08 09:20 My Music
drwxr-xr-x  2 david david       4096 2009-02-06 09:50 My Received Files
drwxr-xr-x  3 david david       4096 2009-02-07 21:46 .nautilus
-rw-r--r--  1 david david          0 2009-02-02 14:50 ncis4.iso
-rw-r--r--  1 david david       1167 2009-02-08 10:32 .nvidia-settings-rc
drwx------  3 david david       4096 2009-02-07 06:00 .openoffice.org2
drwxr-xr-x  3 david david       4096 2009-02-01 09:07 Pictures
-rw-r--r--  1 david david        675 2009-01-31 09:43 .profile
drwxr-xr-x  2 david david       4096 2009-01-31 10:09 Public
drwxr-xr-x  2 david david       4096 2009-01-31 10:09 .pulse
-rw-------  1 david david        256 2009-01-31 10:09 .pulse-cookie
drwx------  4 david david       4096 2009-02-02 13:44 .purple
drwxr-xr-x  2 david david       4096 2009-02-01 08:56 .qt
drwxr-xr-x  2 david david       4096 2009-02-02 06:43 QuickStart
-rw-------  1 david david      54708 2009-02-08 15:01 .recently-used.xbel
-rw-r--r--  1 david david        237 2009-02-08 10:11 .registry
drwxr-xr-x  2 david david       4096 2009-02-01 14:03 rip
drwx------  2 david david       4096 2009-02-07 04:56 .ssh
-rw-r--r--  1 david david          0 2009-01-31 10:15 .sudo_as_admin_successful
drwxr-xr-x  2 david david       4096 2009-01-31 10:09 Templates
-rwxr-xr-x  1 david david     130028 2009-02-07 18:26 testr.rip
drwxr-xr-x  2 david david       4096 2009-02-08 07:52 .themes
drwx------  5 david david       4096 2009-02-07 20:44 .thumbnails
drwx------  2 david david       4096 2009-02-08 15:02 .tsclient
drwxr-xr-x  2 david david       4096 2009-02-02 05:42 .update-manager-core
drwx------  2 david david       4096 2009-01-31 10:09 .update-notifier
drwxr-xr-x  2 david david       4096 2009-02-08 14:39 Videos
drwxr-xr-x  2 david david       4096 2009-02-01 21:39 VIDEO_TS
drwxr-xr-x  2 david david       4096 2009-02-07 20:46 .wapi
-rw-r--r--  1 david david          4 2009-02-01 19:16 .windows-label
drwxr-xr-x  4 david david       4096 2009-02-08 15:01 .wine
-rw-------  1 david david        124 2009-02-08 07:42 .Xauthority
drwxr-xr-x  2 david david       4096 2009-02-03 20:51 .xine
-rw-r--r--  1 david david     200107 2009-02-08 15:29 .xsession-errors
david@david-desktop:~$

---

### Post by cowboy7305 on 2009-02-08
is this what you wanted

---

### Post by taurus on 2009-02-08
```
ls -la ~/.googleearth
```

---

### Post by cowboy7305 on 2009-02-08
do i delete all of them 
sorry i dont know much about this

---

### Post by taurus on 2009-02-08
Since you keep wanting to delete something instead of checking for ownership/permissions first, you can delete ~/.googleearth if you want.

```
rm -rf ~/.googleearth
```

---

### Post by cowboy7305 on 2009-02-08
no i dont want to delete 
i would like it to work

---

### Post by cowboy7305 on 2009-02-08
drwx------  3 david david 4096 2009-02-08 17:31 .
drwxr-xr-x 66 david david 4096 2009-02-08 17:31 ..
drwx------  4 david david 4096 2009-02-08 17:31 Cache
lrwxrwxrwx  1 david david   10 2009-02-08 17:31 instance-running-lock -> /proc/6791
 this is what i get when i open in terminal

---

### Post by taurus on 2009-02-08
```
ls -la ~/.googleearth/Cache
```

p.s.  You can also create those two directories by hand and see if Google Earth is happy about them.

```
mkdir ~/googleearth
mkdir ~/googleearth/cache
```
Restart GoogleEarth.

---

### Post by cowboy7305 on 2009-02-08
The first code give me this 
drwx------ 4 david david 4096 2009-02-08 17:31 .
drwx------ 4 david david 4096 2009-02-08 17:43 ..
drwxr-xr-x 2 david david 4096 2009-02-08 17:31 icons
drwxr-xr-x 2 david david 4096 2009-02-08 17:31 models

---

### Post by cowboy7305 on 2009-02-08
the second set tell me files exist
and when i try and run google earth i get same messages as before 
the ones i posted in first mail

---

### Post by taurus on 2009-02-08
How does it, ~/googleearth, exist when it's not on the list from the output in post #8?

```
ls -la ~
```

---

### Post by cowboy7305 on 2009-02-08
when i reran this ls -la ~/.googleearth
this is what came up
david@david-desktop:~$ ls -la ~/.googleearth
total 16
drwx------  4 david david 4096 2009-02-08 17:45 .
drwxr-xr-x 67 david david 4096 2009-02-08 17:42 ..
drwx------  4 david david 4096 2009-02-08 17:31 Cache
lrwxrwxrwx  1 david david   10 2009-02-08 17:45 instance-running-lock -> /proc/7118
drwx------  2 david david 4096 2009-02-08 17:42 Temp
david@david-desktop:~$

---

### Post by cowboy7305 on 2009-02-08
i have no idea iam posting what is said in terminal window to all your codes

---

