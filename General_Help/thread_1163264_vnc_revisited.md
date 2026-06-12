---
title: "vnc revisited"
date: 2009-05-18
forum: General Help
---

### Post by jmasgalas on 2009-05-18
OK. I have read and read different how to's and maybe I am missing something. Is there a definitive step by step guide so that I can set up vnc to connect to display 0. So that if I am not logged in locally I can connect and see the gdm login screen? I can do it on SLES and also on Redhat with ease so there has to be a way.

BTW,
I know about vino but it only works when I am logged in locally. I want to do the same thing except without having to be logged in.

Thanks!

---

### Post by pricetech on 2009-05-18
Have you tried NX from nomachine dot com ??  Get the Client, Node, Server for Linux and the Client for winders.

Just plain works for me.

---

### Post by jmasgalas on 2009-05-19
I have not tried it. I did try to add the repos for nx but it could not find the gpg key. I will try it today and see how it goes. I can't believe you just can't start vino on boot.

---

### Post by jmasgalas on 2009-05-19
I didn't have much luck with nx. I did run into this but can't seem to get it to work. When I add the line to start vino in /etc/gdm/Init/Default I cannot connect. Has anyone got this working on Jaunty?

[http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/)

1. After logging into Ubuntu, open up Remote Desktop option (System -> Preferences -> Remote Desktop)

2. Check “Allow other users to view your desktop” and “Allow other users to control your desktop” - this is to let others, others would be me in my case, take control of this machine

3. Uncheck “Ask you for confirmation” - when VNC is connected, VNC server will ask for a confirmation to local user.  In my case, this machine will not have a local logged user since it does not have a monitor

4. If possible, assign a password - Having a password should be better than not having one even though VNC still lacks encryption and strong authentication

At this point, VNC server is just enabled with some settings; however, Vino server does not start until a user logs in.  This means that Vino server is not running at User Login screen - where a user types username and password.  In my case, this was not feasible since the machine will not have a monitor (nor keyboard/mouse).

5. Edit /etc/gdm/Init/Default - this gets run when gdm starts (at Login Screen)

emacs /etc/gdm/Init/Default

6. Add the following line right before exit 0 at the end of the file - Vino server runs when gdm starts up

/usr/lib/vino/vino-server &

Vino server starts up when gdm starts up; however, when username and password is typed in, gdm kill this vino-server meaning VNC connection will be terminated.  To prevent this,

7. Edit /etc/gdm/gdm.conf with your favorite text editor

emacs /etc/gdm/gdm.conf

8. Find a commented option KillInitClients=true.  Uncomment it and change it to false and save it. - this prevents vino-server from being killed right after login

KillInitClients=false

Now, you should be able to connect to the machine using VNC

---

### Post by pricetech on 2009-05-22
> **jmasgalas said:**
> I have not tried it. I did try to add the repos for nx but it could not find the gpg key. I will try it today and see how it goes. I can't believe you just can't start vino on boot.

If you still want to try NX, just download from nomachine dot com.  They have debs.

---

### Post by HermanAB on 2009-05-22
Install ssh-server.  Then connect like this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

VNC is not secure.  Having it running on a server is almost a guarantee to have your machine hacked.

---

### Post by XCan on 2009-05-22
> **jmasgalas said:**
> I didn't have much luck with nx. I did run into this but can't seem to get it to work. When I add the line to start vino in /etc/gdm/Init/Default I cannot connect. Has anyone got this working on Jaunty?

[http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/](http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/)

1. After logging into Ubuntu, open up Remote Desktop option (System -> Preferences -> Remote Desktop)

2. Check “Allow other users to view your desktop” and “Allow other users to control your desktop” - this is to let others, others would be me in my case, take control of this machine

3. Uncheck “Ask you for confirmation” - when VNC is connected, VNC server will ask for a confirmation to local user.  In my case, this machine will not have a local logged user since it does not have a monitor

4. If possible, assign a password - Having a password should be better than not having one even though VNC still lacks encryption and strong authentication

At this point, VNC server is just enabled with some settings; however, Vino server does not start until a user logs in.  This means that Vino server is not running at User Login screen - where a user types username and password.  In my case, this was not feasible since the machine will not have a monitor (nor keyboard/mouse).

5. Edit /etc/gdm/Init/Default - this gets run when gdm starts (at Login Screen)

emacs /etc/gdm/Init/Default

6. Add the following line right before exit 0 at the end of the file - Vino server runs when gdm starts up

/usr/lib/vino/vino-server &

Vino server starts up when gdm starts up; however, when username and password is typed in, gdm kill this vino-server meaning VNC connection will be terminated.  To prevent this,

7. Edit /etc/gdm/gdm.conf with your favorite text editor

emacs /etc/gdm/gdm.conf

8. Find a commented option KillInitClients=true.  Uncomment it and change it to false and save it. - this prevents vino-server from being killed right after login

KillInitClients=false

Now, you should be able to connect to the machine using VNC

Thank you for the wonderful guide. Will try this on my work computer asap. I almost gave up the whole gdm thingie after seeing that all guides I found dealt with X11VNC. Guess I'm kind of conservative, I generally like to keep installed applications to a minimum. :p However, I truly wonder why there isn't an easy way (like checking a button) to setup the default vnc server to be usable before logging in.

---

### Post by pricetech on 2009-05-22
> **HermanAB said:**
> Install ssh-server.  Then connect like this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

VNC is not secure.  Having it running on a server is almost a guarantee to have your machine hacked.

I'm not the original poster but;  when I run the command you suggest it prompts me about the key, etc. then loads applet 1 though 7 uneventfully then this is what I get:

** (gnome-panel:3060): DEBUG: Adding applet 8.
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:3060): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
** (gnome-panel:3060): DEBUG: Adding applet 9.
** (gnome-panel:3060): DEBUG: Adding applet 10.
** (gnome-panel:3060): DEBUG: Adding applet 11.
** (gnome-panel:3060): DEBUG: Adding applet 12.

(gnome-panel:3060): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3060): DEBUG: Adding applet 13.


and I'm staring at a flashing cursor.  My desktop is now a mixture of my computer and the one to which I'm connecting.  Ctrl + c does get me out of it.

Input ?????

---

