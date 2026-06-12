---
title: "Internet Kiosk - needs to run java applet"
date: 2010-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tjclifford on 2010-07-26
Good day.
I (we) have an Ubuntu 10.04 LTS on an Optiplex 330, and it is locked down by using 
/etc/gdm/custom.conf which has:

[daemon]

out except ssh
AutomaticLoginEnabled=true
AutomaticLogin=kiosk

...and /home/kiosk.xsession has:

xmodmap -e 'keycode 64 = NoSymbol'
xmodmap -e 'keycode 108 = NoSymbol'

metacity &
devilspie &
/usr/bin/firefox

We need to run a java applet on this box, but the applet says it cannot connect 
to the server, via a socketconnection.
The applet also does not write to a log4j file under kiosk mode.

It seems the kiosk user is pretty limited in what it can do.
My question is, can we modify settings to allow the user to access both a network 
address:socket, and to write to (at least one directory/file on ) the hard disk ?

I have already tried a java client.policy file:

grant {
     permission java.security.AllPermission;
};

and I added:

grant Codebase "http://<fake root url for application>/-" {
     permission java.net.SocketPermission "*:<socketnbr>", "connect, resolve";
};

....to no avail.

I don't have the metacity and devilspie config (if they *have* configs), because I 
don't know enough about the two software packages.

Does anyone know enough to give me some hints on where I might get the applet 
to run correctly ?

Thanks to all......

---

### Post by grg3 on 2010-10-19
Maybe you could try using the "deep freeze" routine discussed on this site [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

I suspect it is the devilspie that is limiting the javascript. Try the above and the Firefox extension Public Fox without devilspie and see if that works.

---

