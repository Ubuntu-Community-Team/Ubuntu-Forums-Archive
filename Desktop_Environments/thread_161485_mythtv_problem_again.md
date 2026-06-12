---
title: "mythtv problem again"
date: 2006-04-17
forum: Desktop Environments
---

### Post by Smika on 2006-04-17
Hello,

I am trying to install Mythtv. When  i am in chapter 9.8 of the howo of this forum, I must do this:

export QTDIR=/usr/lib/qt3
./configure --prefix=/usr/local/mythtv-0.19
qmake mythtv.pro
make

Everything works fine, but when i make, there are some errors:

/usr/bin/ld: cannot find -lqt-mt
collect2: ld returned 1 exit status
make[2]: *** [libmythavcodec-0.19.so.0.19.0] Error 1
make[2]: Leaving directory `/opt/scr/mythtv-0.19/libs/libavcodec'
make[1]: *** [sub-libavcodec] Error 2
make[1]: Leaving directory `/opt/scr/mythtv-0.19/libs'
make: *** [sub-libs] Error 2

Can somebody help me?

Thanks,

Smika

---

### Post by Titus A Duxass on 2006-04-17
I also experienced problems upgrading to 0.19 using the how-to, mine started about same place as yours.  I had to mkdir /opt/src first but that did not help.

As an alternative way of upgrading try adding Hunters [http://kaisman.free.fr/dotclear/index.php?2006/02/27/ubuntu-510-the-breezy-badger-16-thehunterws-ubuntu-repository](http://kaisman.free.fr/dotclear/index.php?2006/02/27/ubuntu-510-the-breezy-badger-16-thehunterws-ubuntu-repository)

Remember to add the key first, do this:

gpg --keyserver subkeys.pgp.net --recv-keys 3BC2083F

Then do this:

gpg --export --armor 3BC2083F | sudo apt-key add -

Then add these to your sources.list:

deb [http://deb.thehunter.ws/](http://deb.thehunter.ws/) breezy mythtv-stable
deb-src [http://deb.thehunter.ws/](http://deb.thehunter.ws/) breezy mythtv-stable

Do:
apt-get update; apt-get upgrade

You may find some packages will be left behind, if so do:

apt-get dist-upgrade.

I did everything as above and now have MythTV-0.19 working.

Hope it helps.

---

### Post by Smika on 2006-04-17
I do what you Said, but when I do:

export QTDIR=/usr/lib/qt3
./configure --prefix=/usr/local/mythtv-0.19
qmake mythtv.pro
make

It gives me the same errors. Or must I install it now from the repository?

Thanks,

Smika

---

### Post by Titus A Duxass on 2006-04-17
Smika,
My alternative is an alternative.  You do not have to follow the how-to anymore.

Install MythTV-0.19 through the repositories, I did the same thing 2 days ago.

---

### Post by slipinsky on 2006-07-08
i am having these errors can someone help

Mythfrontend terminal output

2006-07-08 15:25:25.103 LiveTV not successfully started
2006-07-08 15:25:25.130 Changing from None to WatchingLiveTV
2006-07-08 15:25:25.134 Changing from None to None
2006-07-08 15:25:25.190 Enable DPMS
2006-07-08 15:25:25.202 Using protocol version 15
2006-07-08 15:25:25.334 Using protocol version 15
2006-07-08 15:25:25.471 Using protocol version 15
2006-07-08 15:25:25.635 Using protocol version 15
2006-07-08 15:25:25.780 Using protocol version 15
2006-07-08 15:25:25.948 Using protocol version 15
2006-07-08 15:25:26.114 Using protocol version 15
2006-07-08 15:25:26.270 Using protocol version 15
2006-07-08 15:25:26.430 Using protocol version 15
2006-07-08 15:25:26.599 Using protocol version 15
2006-07-08 15:25:26.762 Using protocol version 15
2006-07-08 15:25:26.928 Using protocol version 15
2006-07-08 15:25:27.076 Using protocol version 15
2006-07-08 15:25:27.245 Using protocol version 15
2006-07-08 15:25:27.330 Using protocol version 15
2006-07-08 15:25:27.681 Disable DPMS
2006-07-08 15:25:27.936 RemoteFile::Read() failed in RingBuffer::safe_read().
2006-07-08 15:25:28.170 RemoteFile::Read() failed in RingBuffer::safe_read().
2006-07-08 15:25:28.390 RemoteFile::Read() failed in RingBuffer::safe_read().
2006-07-08 15:25:28.618 RemoteFile::Read() failed in RingBuffer::safe_read().
2006-07-08 15:25:28.847 RemoteFile::Read() failed in RingBuffer::safe_read().
2006-07-08 15:25:29.080 RemoteFile::Read() failed in RingBuffer::safe_read().
Couldn't read file: rbuf://127.0.0.1:6543/var/cache/mythtv//ringbuf1.nuv



from backend server
Error getting codec params
IVTV_IOC_G_CODEC:: Bad address
2006-07-08 15:25:08.375 TVRec: Recording Prematurely Stopped
2006-07-08 15:25:09.932 MainServer::HandleAnnounce Playback
2006-07-08 15:25:09.932 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:10.072 MainServer::HandleAnnounce Playback
2006-07-08 15:25:10.072 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:10.215 MainServer::HandleAnnounce Playback
2006-07-08 15:25:10.215 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:10.374 MainServer::HandleAnnounce Playback
2006-07-08 15:25:10.374 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:10.544 MainServer::HandleAnnounce Playback
2006-07-08 15:25:10.544 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:10.704 MainServer::HandleAnnounce Playback
2006-07-08 15:25:10.704 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:10.874 MainServer::HandleAnnounce Playback
2006-07-08 15:25:10.874 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.035 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.035 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.193 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.193 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.363 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.363 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.523 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.523 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.683 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.683 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.850 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.850 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.908 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.908 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.952 MainServer::HandleAnnounce Playback
2006-07-08 15:25:11.953 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:11.963 adding: ubuntu as a remote ringbuffer
2006-07-08 15:25:11.975 Changing from None to WatchingLiveTV
Error getting codec params
IVTV_IOC_G_CODEC:: Bad address
2006-07-08 15:25:12.025 TVRec: Recording Prematurely Stopped
2006-07-08 15:25:13.570 MainServer::HandleAnnounce Playback
2006-07-08 15:25:13.571 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:13.715 MainServer::HandleAnnounce Playback
2006-07-08 15:25:13.716 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:13.859 MainServer::HandleAnnounce Playback
2006-07-08 15:25:13.860 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.064 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.065 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.200 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.201 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.339 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.340 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.510 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.511 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.653 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.654 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.820 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.821 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:14.981 MainServer::HandleAnnounce Playback
2006-07-08 15:25:14.982 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:15.145 MainServer::HandleAnnounce Playback
2006-07-08 15:25:15.146 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:15.313 MainServer::HandleAnnounce Playback
2006-07-08 15:25:15.314 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:15.479 MainServer::HandleAnnounce Playback
2006-07-08 15:25:15.480 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:15.559 MainServer::HandleAnnounce Playback
2006-07-08 15:25:15.560 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:15.637 MainServer::HandleAnnounce Playback
2006-07-08 15:25:15.637 adding: ubuntu as a client (events: 0)
2006-07-08 15:25:15.661 adding: ubuntu as a remote ringbuffer
2006-07-08 15:25:15.723 Changing from None to WatchingLiveTV


please help

---

