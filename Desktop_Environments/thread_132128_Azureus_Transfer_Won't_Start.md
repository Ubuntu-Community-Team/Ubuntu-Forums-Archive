---
title: "Azureus Transfer Won't Start"
date: 2006-02-17
forum: Desktop Environments
---

### Post by kimvall on 2006-02-17
After reinstalling my Linux machine a week or two ago, Azureus simply refuses to work; the transfers simply won't start.

And updating it to version 2.4 works without a problem, and the correct version of Java seems to be used; but still no transfers.

I have no firewall in the way, yet most Azureus WHOTO's seem to think that installing and configuring Firestarter is a must. I've tried using it, and not; but the results is always the same; the transfers refuses to start.

When I start Azureus, I get the error message that the 6881 port is in use and I need to check so that no other program or another instance of Azureus is using it.

I tried changing the UDP/TCP listening port to 6882 but it doesn't improve anything. The only difference is that the next time I start Azureus, I get the same error message but this time it's refering to port 6882 instead.

Any ideas anyone? Seems that this is some sort of NAT related problem. But I know very little on the subject at hand.

Here's the code I use to install Azureus:

sudo aptitude -r -y install sun-j2re1.5
sudo aptitude -r -y install libcommons-cli-java
sudo aptitude -r -y install liblog4j1.2-java
sudo aptitude -r -y install libseda-java
sudo aptitude -r -y install libswt-gtk-3.1-java
wget [http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb](http://ftp.us.debian.org/debian/pool/contrib/a/azureus/azureus_2.3.0.6-1_all.deb)
sudo dpkg -i azureus_2.3.0.6-1_all.deb
sudo rm azureus_2.3.0.6-1_all.deb
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java

Thanks in advance.

---

### Post by kimvall on 2006-02-17
"Remember, don't use ports in the 6881-6999 range - change it now if you still do, despite Azureus' default port being 6881."

"The NAT status indicator in the status area is derived from the NAT status of individual torrents. It will show a red indicator if none of your active torrents have been green in the life of the Azureus session. Red therefore does not indicate a definite NAT problem as you may have an active torrent that has never received an incoming connection due to it having only seeds (for example)."

Well, duh... I changed the port to 7000 and it worked like a charm.

And NO Firestarter is needed.

---

