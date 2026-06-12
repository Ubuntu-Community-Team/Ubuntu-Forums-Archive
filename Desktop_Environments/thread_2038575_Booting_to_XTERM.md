---
title: "Booting to XTERM"
date: 2012-08-06
forum: Desktop Environments
---

### Post by abasel on 2012-08-06
I want to boot my system directly to XTERM and then have it automatically run rdesktop.

How do I do this all from the command line?

If rdesktop is exited, instead of dropping to the xterm command line I would like one of the following to happen (listed in order of preference)
1) Call the rdesktop app again
2) Reboot the machine to repeat the process

---

### Post by abasel on 2012-08-08
Got it sorted, and here's how:

Using a minimal install of Ubuntu 8.04 (I tried the new versions but they would not work on my hardware) I installed Ubuntu so that it logs on automatically into an XTERM, executing RDESKTOP in the process.

**Step 1**
Download the mini install ISO and create a boot CD.
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installeri386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installeri386/current/images/netboot/mini.iso")

**Step 2**
Once installed do the following:

```
sudo apt-get update
sudo apt-get install xorg xterm gdm gksu --no-install-recommends
sudo apt-get install rdesktop
sudo service gdm start

```

**Step 3**
Create a file called Default in /etc/gdm/PostLogin (there is a sample file there that you can copy) and add the following line so that the rdp client runs automatically on login.

```
rdesktop -d domain -g 100% ip -4
```

Where domain is the domain name and ip is the IP address of the terminal server.

**Step 4**
Create a guest user to be used for the auto log on. I called this account guest.

```
adduser guest
```

**Step 5**
Edit /etc/gdm/gdm.conf to set up the auto logon as well as a theme error that seems to occur with the minimal install (something to do with Human.xml)

```
AutomaticLogin=guest
AutomaticLoginEnable=True

TimedLogEnable=true
TimedLogin=guest
TimedLoginDelay=0

GtkTheme=circles
GraphicalTheme=circles
```

These entries are scattered through out the file so you will need to search for them

**Final Comment**
Some people might prefer to set TimedLogEnable to false and then set the guest password to something simple like "guest". This will stop the continual logging in, requiring the end-user to enter guest/guest before accessing the RDP session.

---

