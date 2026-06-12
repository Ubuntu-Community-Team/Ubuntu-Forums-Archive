---
title: "Ubuntu remote via Windows"
date: 2012-02-14
forum: Desktop Environments
---

### Post by pbhound on 2012-02-14
I have an Ubuntu 10.04 LTS box that I am using for FOG, I am trying to remote connect to it using Windows 2008 server (I'm using XRDP). I can connect just fine but the problem that I am having is that the remote session that I get has no authority over anything in the system (Ubuntu). what I would like to do is to be able to log in with the same credentials and authorization as the Ubuntu administrator has. as it sits right now when I remote into the Ubuntu box as the supposed admin account I cannot do anything that that user is supposed to be able to do i.e. perform updates, browse HD's etc.

any suggestions?

I would like to not have to be infront of the physical machine each time that I wish to perform any type of maintenance actions.

thank you in advance.

---

### Post by hildenbrandsteven on 2012-02-14
Ssh?

---

### Post by pbhound on 2012-02-14
> **hildenbrandsteven said:**
> Ssh?

I would like to retain the use of the GUI as I know enough about Ubuntu to make me dangerous in a terminal window.

---

### Post by perspectoff on 2012-02-14
The Ubuntu box should be running OpenSSH server. If it is logged into a user account, it can run X11VNC server as well.

The Windows box can connect through SSH using Putty.

The older versions of Windows ran a version of Putty that took a little fiddling to become compliant with OpenSSH standards ( see [http://ubuntuguide.org/wiki/Ubuntu:Oneiric#PuTTY](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#PuTTY) ), but I think newer Putty versions are OpenSSH compliant in regards to the SSH security keys.  

Then you can tunnel VNC through the SSH connection and have secure control over the Ubuntu desktop. I like UltraVNC on Windows (because file transfer is built in) but TightVNC is a good alternative.

See

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Remote_Access)

---

### Post by pbhound on 2012-02-14
> **perspectoff said:**
> The Ubuntu box should be running OpenSSH server. If it is logged into a user account, it can run X11VNC server as well.

The Windows box can connect through SSH using Putty.

The older versions of Windows ran a version of Putty that took a little fiddling to become compliant with OpenSSH standards ( see [http://ubuntuguide.org/wiki/Ubuntu:Oneiric#PuTTY](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#PuTTY) ), but I think newer Putty versions are OpenSSH compliant in regards to the SSH security keys.  

Then you can tunnel VNC through the SSH connection and have secure control over the Ubuntu desktop. I like UltraVNC on Windows (because file transfer is built in) but TightVNC is a good alternative.

See

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Remote_Access)

thank you for the info i will look at it tomorrow when i have time.

Im not worried about the security as the two machines are in my house on a seperate network than my normal network.

---

### Post by pbhound on 2012-02-16
> **perspectoff said:**
> The Ubuntu box should be running OpenSSH server. If it is logged into a user account, it can run X11VNC server as well.

The Windows box can connect through SSH using Putty.

The older versions of Windows ran a version of Putty that took a little fiddling to become compliant with OpenSSH standards ( see [http://ubuntuguide.org/wiki/Ubuntu:Oneiric#PuTTY](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#PuTTY) ), but I think newer Putty versions are OpenSSH compliant in regards to the SSH security keys.  

Then you can tunnel VNC through the SSH connection and have secure control over the Ubuntu desktop. I like UltraVNC on Windows (because file transfer is built in) but TightVNC is a good alternative.

See

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Remote_Access)

in order to use UltraVNC wouldnt i have to install it onto the Ubuntu?

---

