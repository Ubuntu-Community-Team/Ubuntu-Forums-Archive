---
title: "Make Computer BEEP on startup"
date: 2009-02-08
forum: General Help
---

### Post by BuntuFreak on 2009-02-08
I'm using my Ubuntu Desktop installation as a server, more specifically a file server. Or I should say just decided to do so since my Hardware just doesn't have the "power" to be used as a desktop anymore.

And everything is working great. Since I don't plan on using the machine to do any other work other than being able to copy files to it and read files from it, I wouldn't need to have it connected to a monitor. Now what I want to do is that when I power up the sucker, I need to know it's all booted up so other computers on my network can start accessing the files on it. But since I don't have a  monitor connected, how do I know that? My idea - make the computer beep 5 times after its booted up.

So I tried the following. I thought it would work. But it doesn't.

1)Created file /etc/rc.load
2)Put the following in it : beep -l 900 -r 5 -f 500
3)chmod 755 /etc/rc.load

I type command in 2) above in my terminal, I hear 5 beeps. So I think that part is okay. But my computer is not "looking" at /etc/rc.load. Or maybe I've put this in the wrong file. Or whatever. Just need a solution.

Thanks in advance for your time and help.

---

### Post by markusf21 on 2009-02-08
I don't know if it will work but you could try putting that file in your sessions. system> preferences> sessions

---

### Post by BuntuFreak on 2009-02-08
> **markusf21 said:**
> I don't know if it will work but you could try putting that file in your sessions. system> preferences> sessions

Interesting idea. But I don't think it'll work. Sessions are in effect AFTER you log on. Remember, all I've done is turn the power ON and OS should be waiting at the Login Prompt. I only need to be at the prompt for my files to be accessible over my network. That's the whole point. If I was going to Logon, I'll need a monitor now, right? ;-)

Which brings me to another thing. I'll like the beeps to happen even when the computer comes off "Suspend". That way I can use the Power Options to automatically suspend my computer at night and then simply press power button once, hear the beeps and know I'm good.

P.S. I have another related question about getting the computer off Suspend when a network connection is attempted over my LAN. But that is a topic for another thread.

---

### Post by markusf21 on 2009-02-08
you could set it to auto login. it would atleast do what you need till find a better way

---

### Post by cariboo on 2009-02-08
The OP is running the server version, there is no gui, hence no auto login.

I found this [howto]("http://blog.softdux.com/everything-todo-with-linux/linux-howtos/how-to-enable-a-startup-shutdown-sound-on-linux-servers.html") to do what you want. there is a link to a deb in the how to.

Jim

---

### Post by markusf21 on 2009-02-08
> **cariboo907 said:**
> The OP is running the server version, there is no gui, hence no auto login.

I found this [howto]("http://blog.softdux.com/everything-todo-with-linux/linux-howtos/how-to-enable-a-startup-shutdown-sound-on-linux-servers.html") to do what you want. there is a link to a deb in the how to.

Jim
he said he was using the desktop version as a server

---

### Post by srt4play on 2009-02-08
> **cariboo907 said:**
> The OP is running the server version, there is no gui, hence no auto login.

[QUOTE=BuntuFreak]I'm using my Ubuntu Desktop installation as a server[/QUOTE]

I agree with setting it to autologin, and I would also enable remote desktop for easy administration of your server.

---

### Post by geirha on 2009-02-08
Putting the beep command in that init script should work, however, the init-script is called /etc/rc.local, not /etc/rc.load.

Another thing you can do is to ping your computer from one of the others.

```
ping <ip address>
```

ping will keep pinging until you hit Ctrl+c. Once the computer's network is up, you'll start getting ping replies.

---

### Post by BuntuFreak on 2009-02-08
Yes, I'm running Ubuntu Desktop not Ubuntu Server.

Yes, I AM using my desktop as a "file server".

No, I don't want to use auto login since it seems drastic and a little insecure. [-X

Remote Desktop - Now that is a great idea, and so obvious. Just in case I want to go and delete some files from my shared disk, that would be a good way for me to do it. Thanks. =D>

Finally, rc.local vs rc.load. That works perfectly. :-\"

I'll start a different thread for WOL and Suspend/Hibernate questions.

Best.

---

