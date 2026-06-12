---
title: "https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234727"
date: 2009-04-10
forum: General Help
---

### Post by mmm11105 on 2009-04-10
Got this bug

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234727](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/234727)
(Sudo seg-fault)

Someone's made a .patch to fix it but I can't figure out how to install it.

Help Please :cry: I never got a chance to install some important software

---

### Post by ibuclaw on 2009-04-10
```
cd ~/Desktop

apt-get source sudo

cd sudo*

wget http://launchpadlibrarian.net/21261955/sudo.patch -O- | patch -p1

dpkg-buildpackage -rfakeroot
```

If it fails to build because of missing build-deps, you'll have to reboot into **recovery mode** and go into "Root Terminal with Networking".
```
apt-get build-dep sudo
```

You will also require the use of **recovery mode** to install the application too.
```
cd /home/**username**/Desktop/
dpkg -i sudo*deb
```

Regards
Iain

---

### Post by mmm11105 on 2009-04-11
When I boot to the recovery Menu there is no "Root Terminal with Networking Option"

apt-get source sudo Returns this

mmlinux@mmlinux:~/Desktop$ apt-get source sudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 620kB of source archives.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main sudo 1.6.9p17-1ubuntu2.1 (dsc) [1135B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main sudo 1.6.9p17-1ubuntu2.1 (tar) [594kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-updates/main sudo 1.6.9p17-1ubuntu2.1 (diff) [25.4kB]
Fetched 620kB in 1s (402kB/s)
sh: dpkg-source: not found
Unpack command 'dpkg-source -x sudo_1.6.9p17-1ubuntu2.1.dsc' failed.
Check that the 'dpkg-dev' package is installed.
E: Child process failed

---

### Post by ibuclaw on 2009-04-12
Are you sure? What version of Ubuntu are you running? It is called **netroot** in the recovery menu.

Regards
Iain

---

### Post by mmm11105 on 2009-04-12
8.10 Latest Kernel

netroot is missing.

My Network connect is ethernet though a router.

---

### Post by ibuclaw on 2009-04-12
> **mmm11105 said:**
> 8.10 Latest Kernel

netroot is missing.

My Network connect is ethernet though a router.
That's ok, to get networking up and running, just enter the **root** shell then, and then:
```
cd /etc/init.d
```
And start the following services:

```
./dbus start
./hal start
./NetworkManager start
./avahi-daemon start
```

At the end of that, running
```
ifconfig
```
Should show the **eth0** device. And running:
```
apt-get update
```
Should pull all updated sources from the website.

This will confirm that your network is up and working, and you will be able to continue with:
```
apt-get install build-essential fakeroot
```
and
```
apt-get build-dep sudo
```
as I mentioned earlier in PM.

Then continue with what I mentioned above:
```

cd
apt-get source sudo
cd sudo*
wget http://launchpadlibrarian.net/21261955/sudo.patch -O- | patch -p1
dpkg-buildpackage -rfakeroot
cd ../
dpkg -i sudo*.deb
apt-get install -f
```

Then reboot, and hopefully the patch will have worked.

Regards
Iain

---

### Post by mmm11105 on 2009-04-13
Patched. Still have same old seg-fault

---

