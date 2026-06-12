---
title: "In need of a very simplistic CLI torrent client..."
date: 2009-05-07
forum: General Help
---

### Post by ownaginatious on 2009-05-07
I recently set up a new web/file server which uses Jaunty 9.04. So far I've gotten Apache Tomcat, vsFTP and samba working perfectly. The last component I need is a light weight torrent client, which can operate in the background and be controlled through a web interface. I was using azureus for this, but as far as I know, it can only work while the GUI is running. Azureus is also a slow resource hogging piece of ****, so I'd rather avoid it.

Does anyone know of a replacement torrent client for my needs?

Thanks,

Dillon

---

### Post by BslBryan on 2009-05-07
Hello, ownaginatious. :-)

May I suggest you trying out Bittornado?

I believe it's even in Synaptic Package Manager. :-)

Try ```
sudo apt-get install bittornado
```

If there's no package found, go [here]("www.bittornado.com") for the download link.  

I hope I've been of some help. :-)  Do keep me updated. 

Best to you, ownaginatious. :-)

---

### Post by ownaginatious on 2009-05-07
Thanks BslBryan!

I tried installing TorrentFlux (web interface to bittornado) and I unfortunately have run into some problems.

The main problem is that I don't use Apache2 as my webserver; I use Apache Tomcat, since it allows me to run JSP pages and servlets. Ubuntu doesn't "recognize" this, so when I installed TorrentFlux, it was telling me that I have no web server installed, which means no auto-configuration.

Would anyone perhaps know how to get around this? I know this may sound stupid, but can I get Apache2 to run servlets and JSP pages or just merge Apache2 and Tomcat?

Thanks again,

Dillon

---

### Post by kpkeerthi on 2009-05-07
You might be interested in [wtorrent + rtorrent]("http://www.wtorrent-project.org/trac/"). 

[Install Help]("http://www.wtorrent-project.org/trac/wiki/DebianInstall")

---

### Post by ownaginatious on 2009-05-07
Thanks, I actually like the look of this rTorrent and wTorrent better :)

I still have the problem of needing both Tomcat and Apache2 simultaneously though. Is it possible to have them at the same time, but have one running over a different port? Azureus seemed to do something like that, where my tomcat server ran on port 80 while the azureus webclient ran on 6886 I think. That all seemed to occur automatically though :p.

Even better - is it possible to install support for JSP and Servlets in Apache2?

---

### Post by kpkeerthi on 2009-05-07
> **ownaginatious said:**
> 
Even better - is it possible to install support for JSP and Servlets in Apache2?

Yes it is possible. I have done that in windows but have not tried in linux. Here is a [how to for linux]("http://www.howtoforge.com/apache2_tomcat5_mod_jk_integration"). (most of the packages can be installed from Ubuntu repository)

---

### Post by FluffyElmo on 2009-05-07
Transmission also has a very nice web ui. I believe all you have to do is enable it in the preferences if you have a desktop, it can also be installed for command line use via the transmission-cli package. [http://www.transmissionbt.com/](http://www.transmissionbt.com/)

---

### Post by ownaginatious on 2009-05-10
> **FluffyElmo said:**
> Transmission also has a very nice web ui. I believe all you have to do is enable it in the preferences if you have a desktop, it can also be installed for command line use via the transmission-cli package. [http://www.transmissionbt.com/](http://www.transmissionbt.com/)

I would really like to look into that... but the documentation on how to set anything up is absolutely terrible. There is literally nothing about how to get the cli or web interface working. All that I can find are stupid documents saying "just go to the config files", which just so happen to not exist....

---

### Post by ownaginatious on 2009-05-10
> **BslBryan said:**
> Hello, ownaginatious. :-)

May I suggest you trying out Bittornado?

I believe it's even in Synaptic Package Manager. :-)

Try ```
sudo apt-get install bittornado
```

If there's no package found, go [here]("www.bittornado.com") for the download link.  

I hope I've been of some help. :-)  Do keep me updated. 

Best to you, ownaginatious. :-)

Thanks for the recommendation!

Well, I eventually got bittornado installed, but I only think it's okay. The WebUI is pretty convoluted in my opinion, and I find the method of launching torrents quite awkward (I need to tell it to start seeding and leeching?!). I also don't understand why there is a whole account system :/.

I kind of like the azureus web interface better since it's a lot easier to use.

Also, I don't know if this is only me or not, but whenever I start downloading at higher speeds (around 200 KB/s), torrentflux begins to severely interfere with the speed of Samba for some reason, which causes movies and stuff I'm watching over the network to lag...

---

### Post by geirha on 2009-05-10
> **ownaginatious said:**
> I would really like to look into that... but the documentation on how to set anything up is absolutely terrible. There is literally nothing about how to get the cli or web interface working. All that I can find are stupid documents saying "just go to the config files", which just so happen to not exist....

The web interface is started by default when you run the daemon, but it only listens on localhost:9091, so you need to edit the config file to open for other IPs.

[http://trac.transmissionbt.com/wiki/HeadlessUsage](http://trac.transmissionbt.com/wiki/HeadlessUsage)

EDIT:
The file you need to edit/create should be $HOME/.config/transmission-daemon/settings.json

[http://trac.transmissionbt.com/wiki/EditConfigFiles](http://trac.transmissionbt.com/wiki/EditConfigFiles)

---

### Post by 3rdalbum on 2009-05-10
I second the suggestion of Transmission. Don't read the documentation - just install the transmission-cli package, run the "transmission-daemon" program at bootup, and access the web interface on port 9091.

You can send commands via the "transmission-remote" program; read the man page for details.

---

### Post by ownaginatious on 2009-05-10
Okay... maybe I'm missing something here; but this doesn't appear to be working at all.

If I run "transmission-daemon" or "sudo transmission daemon" in the command line; nothing happens. When I go to my web browser following and type "http://serverip:9091/transmission/web", nothing is found.

I also checked the GUI version of transmission and there is **no** mention of a web interface to enable anywhere; like it said I should be able to "enable" in the documents on the developers website.

Can anyone help me out here? :(

---

### Post by collinp on 2009-05-10
> **ownaginatious said:**
> Okay... maybe I'm missing something here; but this doesn't appear to be working at all.

If I run "transmission-daemon" or "sudo transmission daemon" in the command line; nothing happens. When I go to my web browser following and type "http://serverip:9091/transmission/web", nothing is found.

I also checked the GUI version of transmission and there is **no** mention of a web interface to enable anywhere; like it said I should be able to "enable" in the documents on the developers website.

Can anyone help me out here? :(

No, its [http://serverip:9091](http://serverip:9091) only, nothing more. Also, I saw something in the preferences mentioning the web interface, not sure where though.

---

### Post by ownaginatious on 2009-05-10
> **Hellow said:**
> No, its [http://serverip:9091](http://serverip:9091) only, nothing more. Also, I saw something in the preferences mentioning the web interface, not sure where though.

I guess their documents are wrong then. On a side note though; that doesn't work either. I'm going to try restarting the computer to see what happens.

[EDIT]
Restarting didn't help at all...

---

### Post by geirha on 2009-05-10
Did you whitelist the ip of the computer you are trying to view the web page from in .config/transmission-daemon/settings.json?

```

{
    "rpc-enabled": 1,
    "peer-port" : 9091,
    "rpc-whitelist": "127.0.0.*,[COLOR="Blue"]192.168.*.*[/COLOR]"
}

```

Also, check that it is listening on port 9091 on the server.
```
netstat -nap | grep -w 9091
```

---

### Post by ownaginatious on 2009-05-11
Hmm, I tried that too. Nothing's happening.

Is it possible that the version of Transmission in my repositories is old and doesn't include the web interface?

---

### Post by geirha on 2009-05-11
No, it's had that web interface built in for a long time. However, I just did something I should've done from the start; checked the 9.04 packages of transmission. I see now that transmission-daemon has been put in a [separate package](http://packages.ubuntu.com/jaunty/i386/transmission-daemon/filelist), and gotten an init script. That means that once you install the transmission-daemon package, transmission-daemon will be started during boot, and reads its configuration from /etc. /etc/transmission-daemon/settings.json to be exact. So try editing that file ```
EDITOR=vim sudoedit /etc/transmission-daemon/settings.json
``` then restart it with ```
sudo /etc/init.d/transmission-daemon restart
```

---

### Post by ownaginatious on 2009-05-11
Ahh, now that makes more sense; thanks Geirha. I accidentally neglected to mention this before, but I've actually reinstalled my file server with Debian Linux (Lenny) since I originally posted this thread. It works the same (except fast on my piece of crap computer) in the command line.

Anyway; I finally got the transmission-daemon installed, but there still appears to be no web page coming up :(

Whenever I edit settings.json it gets reverted back to how it originally as soon as I restart the daemon.

Anyone know what's up with that?

---

### Post by geirha on 2009-05-11
Sounds like the daemon saves its current settings to that file when it closes then, which means that you might be able to configure it with tranmission-remote while the daemon is running. However, if you first stop transmission-daemon, then edit settings.json, and then start it again, your settings should take effect. 
```

sudo /etc/init.d/transmission-daemon stop
EDITOR=vim sudoedit /etc/transmission-daemon/settings.json
sudo /etc/init.d/transmission-daemon start

```

---

### Post by ownaginatious on 2009-05-11
I kind of feel dumb for not realizing that earlier -.-||

Anyway, it works great now :D The interface feels a lot more user friendly to me than does TorrentFlux :p. Clean and simple.

Thanks for your help everyone; especially Geirha. I must say Geirha, you have the quickest response time I've ever seen on a forum 0.o. Thanks again for your help. :)

---

### Post by geirha on 2009-05-11
Hehe, well in the User CP I've set it so that I'm automatically subscribed to threads I post in, and whenever a new post is posted, I get a mail about it, which is checked every 5 minutes by a firefox plugin. So I generally get a notification of a new post within 5 minutes.

Anyway, I just realized you might run into a permission issue. Transmission-daemon is probably running as a separate user, likely called transmission, so that user needs write access to the destination folder you choose, and the files you download will be owned by that user. If you don't know how to do handle the permissions and onwership, feel free to post some more questions.

---

### Post by ownaginatious on 2009-05-23
Hmm, I do appear to be having some problems with the permissions. I've determined that the user who is being used for downloading the torrents is called debian-transmission. I tried adding my account to the group, but I'm still unable to modify the downloaded files.

Is there a way to fix all this through the command line? I only have the fluxbox interface on my computer; so any solutions in gnome are out of the question.

Sorry to be so vague, but I'm really tired and should be getting some sleep :p

---

### Post by geirha on 2009-05-23
I had a look at this in a VM. The files it downloads get permissions 755 (dirs) and 644 (files), which means only the debian-transmission user has write access to it. If they had 775 and 664 permissions, you would get write permission to all those files via the group membership.

One way to have transmission create the files with 775/664 permissions, is to change the umask it uses. You do that by editing the init script ```
sudoedit /etc/init.d/transmission-daemon
```
And add the command "umask 0002" just before start_daemon
```

case "$1" in
    start)
        log_daemon_msg "Starting bittorrent daemon" "$NAME"
        [COLOR="Blue"]umask 0002[/COLOR]
        start_daemon
        log_end_msg 0
        ;;

```

After that all new files and folders that transmission-daemon creates will have 775/664 permissions. The files already created you'll need to change manually. The following command should do the trick
```
find /var/lib/transmission-daemon/downloads \( -type f -or -type d \) -print0 | sudo xargs -0 chmod g+w
```

Alternatively, since the chmod implementation on debian/ubuntu systems doesn't follow symlinks when you run it recursively, you can also do:
```
sudo chmod -R g+w /var/lib/transmission-daemon/downloads
```

You should now have access to move and delete files.

---

### Post by ownaginatious on 2009-05-23
> **geirha said:**
> I had a look at this in a VM. The files it downloads get permissions 755 (dirs) and 644 (files), which means only the debian-transmission user has write access to it. If they had 775 and 664 permissions, you would get write permission to all those files via the group membership.

One way to have transmission create the files with 775/664 permissions, is to change the umask it uses. You do that by editing the init script ```
sudoedit /etc/init.d/transmission-daemon
```
And add the command "umask 0002" just before start_daemon
```

case "$1" in
    start)
        log_daemon_msg "Starting bittorrent daemon" "$NAME"
        [COLOR="Blue"]umask 0002[/COLOR]
        start_daemon
        log_end_msg 0
        ;;

```

After that all new files and folders that transmission-daemon creates will have 775/664 permissions. The files already created you'll need to change manually. The following command should do the trick
```
find /var/lib/transmission-daemon/downloads \( -type f -or -type d \) -print0 | sudo xargs -0 chmod g+w
```

Alternatively, since the chmod implementation on debian/ubuntu systems doesn't follow symlinks when you run it recursively, you can also do:
```
sudo chmod -R g+w /var/lib/transmission-daemon/downloads
```

You should now have access to move and delete files.

Thanks! Everything worked perfectly! I'll have to remember that umask thing.

> The web interface starts when you run the daemon, but it only listens on localhost:9091, so you need to edit the config file to open for another IPs.

Yup.

---

