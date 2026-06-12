---
title: "Multi user wTorrent, rTorrent"
date: 2009-04-08
forum: General Help
---

### Post by thecheeks on 2009-04-08
So I've spent the last week learning everything in command line since I haven't had much exposure to Linux systems. I've finally given up trying to figure this out on my own, time to ask the experts. Here is what I am trying to do:

I have the user 'seedbox' auto login to GNOME where I will make Boxee or XBMC auto launch too. This way all you do is hit the power button and our media center is on.

Here is where it gets tricky. I want to create a few users that people can SSH into and use rTorrent and wTorrent. I installed both using that script that is in the forums here, which runs rTorrent (not 100% sure actually) on the user 'RT'. Unfortunately, this method means there is only one rTorrent instance running, with only one .rtorrent.rc file. What I want is for rtorrent to be ran on each individual user, that way each user can have their own custom .rtorrent.rc file (different watch folders, download drives).

So how would I configure Lighttpd and wTorrent so that there is a seperate wTorrent per user? I need to keep all bittorrent activity seperate (otherwise wTorrent makes a web user, but all data is still put into the same dir).

Thanks so much!

---

### Post by hyper_ch on 2009-04-08
you can run multiple instances of rtorrent.

---

### Post by thecheeks on 2009-04-08
Of coarse you can run more than one rTorrent, that's not what I'm talking about.

Lighttpd listens on port 5000 for rTorrent activity. Even if you could run another rTorrent on the same port, wTorrent would not be able to tell the difference in activity between the two, it would think it's still looking at one and not split it by user or anything.

What I need to do (and need help figuring out) is how to get Lighttpd to listen on two or more different ports, so that each .rtorrent.rc can use their own port (5000, 5001...)

Once that is done, I would assume I would need to make several copies of wTorrent into folders and 'install' them accordingly, but how would I point those to a specific user anyways?

---

### Post by MSToTheEnd on 2009-04-09
I was going to ask the same thing.

I've just formated my dedicated server to Debian Server. I got my rtorrent+wtorrent running perfectly but now I want to add two more.

I'm gonna try it my way. If I find a solution I'll post it here. if not... i'm gonna ask you :p

Sorry for my english.

---

### Post by thecheeks on 2009-04-09
Sorry for your English? Sounds like your fluent haha.

Glad to see someone else has the same problem. I'll try a few things and let you know how I do too, I'm sure we'll figure this out eventually.

---

### Post by MSToTheEnd on 2009-04-09
[http://www.wtorrent-project.org/trac/wiki/wTorrentInstall](http://www.wtorrent-project.org/trac/wiki/wTorrentInstall)

Check the part where it talks about "Using mod_scgi for apache"

I think it's easier the setup with Apache for what we need to do.

That way you can setup different SCGI ports and you can have several rtorrent+wtorrent running. (Edit the .rtorrent.rc file line scgi_port = localhost:5000 to 5001)

I didn't try it yet.

---

### Post by thecheeks on 2009-04-09
Yeah I just stumbled upon that recently. I don't think lighttpd is good enough to do what we want, I'll prob switch over to apache tonight then, looks like better documentation for multiple setups.

---

### Post by thecheeks on 2009-04-09
I'm still screwing with things but I think I see one problem that I don't know how to overcome. So rTorrent broadcasts info on port 5000, that the SCGI Gateway picks up and relays to wTorrent on port 80. If we add another gateway port (5001), it will still broadcast over port 80 to wTorrent. How do we tell each instance of wTorrent to look at a certain rTorrent and basically ignore the other?

---

### Post by MSToTheEnd on 2009-04-09
I found myself with the same issue.

I don't know how to tell new wtorrent setup to "look" the new rtorrent instance.

I think a friend of mine used virtual host in apache. As soon as I can contact him i'll ask him about it.

---

### Post by thecheeks on 2009-04-09
Keep me updated, I'm fairly sure we're not the only ones looking to do this, and if/when we figure it out we can put out a tutorial of some type.

I feel like the dedicated seedboxes you can rent do this for each user...

---

### Post by MSToTheEnd on 2009-04-10
I've got it working.

This got me so tired :lol:

---

### Post by thecheeks on 2009-04-10
When you catch your breath, let me know ;)

---

### Post by bodhi.zazen on 2009-04-10
IMO easiest way to do this is with screen.

Make a shared user account for rtorrent and start it in a screen session.

When users wish to connect to the server , have them ssh in and connect to the screen session.

You can also run a shared screen session.

[http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/](http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/)

That link may be too secure, relax the permissions a little.

---

### Post by MSToTheEnd on 2009-04-10
> **bodhi.zazen said:**
> IMO easiest way to do this is with screen.

Make a shared user account for rtorrent and start it in a screen session.

When users wish to connect to the server , have them ssh in and connect to the screen session.

You can also run a shared screen session.

[http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/](http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/)

That link may be too secure, relax the permissions a little.

I think we were both looking for a way to set different wtorrent interfaces.

------------

This is the way to make it work:

Edit the config file /etc/apache2/httpd.conf:

Add these lines:

```
SCGIMount /RPC1 127.0.0.1:5001 
SCGIMount /RPC2 127.0.0.1:5002 
SCGIMount /RPC3 127.0.0.1:5003 
SCGIMount /RPC4 127.0.0.1:5004 
SCGIMount /RPC5 127.0.0.1:5005 
SCGIMount /RPC6 127.0.0.1:5006
```

You can use whatever ports you like.

In every DIFFERENT wtorrent installation edit --- > /var/www/wtorrent/conf/user.conf.php this way:

```
define ('RT_DIR', '/RPC1');
```

Set the RT_AUTH DIR to /RPC1 or /RPC2 or /RPC3, etc.

Now in the .rtorrent.rc file (different for every user) set the correct port like this:

```
scgi_port: localhost:5001
```

Now restart the apache server:

```
/etc/init.d/apache2 restart
```

I didn't see information like this anywhere so if you (anyone) create a tutorial at least say that I was the one to share this :p

I mean... i didn't discover nothing new but I solved a problem that everyone has.

I hope you can understand me. My english is not THAT good.

---

### Post by thecheeks on 2009-04-11
Nice! Looks good and make a lot of sense, I was confused what /RPC# was all about, that's where I got hungup. 

One problem though, Apache2 doesn't want to use SCGIMount
>  * Starting web server apache2
Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'SCGIMount', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!


Can't seem to find a good tutorial on getting SCGI with Apache2 to work...

Edit: Nevermind, got it working. Thanks so much! I'll probably write up a tutorial for you since you don't seem so confident on your English haha. All credit to you man ;)

---

### Post by thecheeks on 2009-04-11
How did you properly install Apache2 to work for wTorrent? I don't think I know how to properly install scgi to work with Apache, it doesn't like SCGIMount...

---

### Post by MSToTheEnd on 2009-04-11
```
apt-get install libapache2-mod-scgi
```

Good luck!

---

### Post by thecheeks on 2009-04-11
Got it working :)

---

### Post by Jontox on 2009-04-19
Hi All,

Is there a way to achieve this with lighttpd and not apache2 ?

I was trying to add a second scgi.server in the below conf file

nano /etc/lighttpd/conf-available/10-scgi.conf
      
  ```
scgi.server = (
"/RPC2" => # RT_DIR
( "127.0.0.1" =>
(
"host" => "127.0.0.1", # Ip where rtorrent is listening
"port" => 5000, # Port specified in .rtorrent.rc (First User)
"check-local" => "disable"
)
)
scgi.server = (
"/RPC3" => # RT_DIR
( "127.0.0.1" =>
(
"host" => "127.0.0.1", # Ip where rtorrent is listening
"port" => 5001, # Port specified in .rtorrent.rc (second user)
"check-local" => "disable"
)
)
)
```

But unfortunately it is not working at all when I restart lighttpd service.

Any idea ?

Thanks a lot in advance

Jontox

---

### Post by thecheeks on 2009-04-19
I was having problems with Apache2 so I switched back to Lighttpd, *thought* I was close to figuring it out but failed. 

Yes, if anyone knows how to do this with Lighttpd, please let us know. All we need is multiple instances of /RCP# in scgi.server

---

### Post by DrGkill on 2009-04-20
I'm also working on this (with lighttpd). I'll let you know if I have a solution.

To run rtorrent in background mode, how do you guys do ?

```
nohup su - user -c 'rtorrent'&
``` ?

---

### Post by DrGkill on 2009-04-20
> **MSToTheEnd said:**
> 

In every DIFFERENT wtorrent installation edit --- > /var/www/wtorrent/conf/user.conf.php this way:

```
define ('RT_DIR', '/RPC1');
```

Set the RT_AUTH DIR to /RPC1 or /RPC2 or /RPC3, etc.


So you mean install wtorrent vhost for each users ????

It's a pitty that the documentation is so poor...

---

### Post by Jontox on 2009-04-20
> **DrGkill said:**
> I'm also working on this (with lighttpd). I'll let you know if I have a solution.

To run rtorrent in background mode, how do you guys do ?

```
nohup su - user -c 'rtorrent'&
``` ?

I'm using a VNC desktop with Fluxbox Menu, it is really handy and user-friendly.
You log yourself into VNC Desktop, then run Rtorrent and disconnect from VNC Desktop, everything is running in the background.

There is a nice Tutorial using that method for Utorrent WebUI under linux but it's the same for rtorrent
[http://filesharingtalk.com/vb3/f-guides-and-tutorials-65/t-naqs-complete-setup-guide-linux-seedboxes-fedora-corecentosdebianubuntu-281331]("http://filesharingtalk.com/vb3/f-guides-and-tutorials-65/t-naqs-complete-setup-guide-linux-seedboxes-fedora-corecentosdebianubuntu-281331")

See you

Jontox

---

### Post by thecheeks on 2009-04-20
Sloppy method, better idea would be to SSH to your box, run Screen and run rTorrent inside of it.

I gave up on Lighttpd, sucked it up and got Apache2 working (finally). At least we know it's possible with Apache.

---

### Post by DrGkill on 2009-04-20
> **thecheeks said:**
> Sloppy method, better idea would be to SSH to your box, run Screen and run rTorrent inside of it.


Yep, why not.
But doesn't seems to be super clean as well. 
torrentflux seems to be much more easier after all.

---

### Post by Jontox on 2009-04-21
As for lighttpd.

Someone told me to modify 10-scgi.conf this way (you will have second user using port 5001 and RPC3)

```
scgi.server = (
"/RPC2" => # RT_DIR
( "127.0.0.1" =>
(
"host" => "127.0.0.1", # Ip where rtorrent is listening
"port" => 5000, # Port specified in .rtorrent.rc
"check-local" => "disable"
)
)
"/RPC3" => # RT_DIR
( "127.0.0.1" =>
(
"host" => "127.0.0.1", # Ip where rtorrent is listening
"port" => 5001, # Port specified in .rtorrent.rc
"check-local" => "disable"
)
)
)
``` 

Unfortunately when I'm trying that and restarting lightttpd server, I'm getting the following issue

```
* Stopping web server lighttpd [ OK ]
* Starting web server lighttpd                                                 
2009-04-21 09:52:10: (configfile.c.855) source: /etc/lighttpd/conf-enabled/10-scgi.conf line: 10 pos: 9 parser failed somehow near here: /RPC3
2009-04-21 09:52:10: (configfile.c.855) source: /usr/share/lighttpd/include-conf-enabled.pl line: 3 pos: 1 parser failed somehow near here: (EOL)
2009-04-21 09:52:10: (configfile.c.855) source: /etc/lighttpd/lighttpd.conf line: 156 pos: 1 parser failed somehow here: (EOL) [[COLOR="Red"]fail[/COLOR]]
```

Any help ?

Thanks in advance

Jontox

---

### Post by DrGkill on 2009-04-21
Try using a syntax much more like this :

```
scgi.server = (
                "/RPC2"=>
                (
                        "127.0.0.1" =>
                        (
                                "host" => "127.0.0.1",
                                "port" => 5000,
                                "check-local" => "disable"
                        )
                )**[COLOR="Red"],[/COLOR]** # <------ COMMA
                "/RPC3"=>
                (
                        "127.0.0.1" =>
                        (
                                "host" => "127.0.0.1",
                                "port" => 5001,
                                "check-local" => "disable"
                        )
                )
)
```

The comma between the two definition is important.

---

### Post by thecheeks on 2009-04-21
Holy crap, if I didn't get it working because I was missing only a comma... haha

---

### Post by gMonk on 2009-12-08
Was looking at this thread in hopes to set up rtorrent + wtorrent for three users.  I did my best to try and replicate your results but with no success.  Was wondering any of you guys possibly made a tutorial for on this?  Thank you

---

