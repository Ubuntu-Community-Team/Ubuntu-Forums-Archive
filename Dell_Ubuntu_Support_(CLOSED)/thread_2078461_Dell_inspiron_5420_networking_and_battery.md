---
title: "Dell inspiron 5420 networking and battery"
date: 2012-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by andriansah on 2012-10-31
Dear all
I compile of how to manage networking and extend battery using ubuntu 12.04 64bit, i think it will work with 32 bit

For Networking

[http://andri.andriani.web.id/wired-network-and-wireless-network-dell-inspiron/](http://andri.andriani.web.id/wired-network-and-wireless-network-dell-inspiron/)

[INDENT]To activate wire network

Install compat wireless with this version

compat-wireless-2012-02-28-p

./scripts/driver-select alx

make

sudo make install

reboot and plug in your wire network

 

After you wired network up now its time fire up the wireless

download this file

It’s here: [http://wielki.tk/vostro/debs/wlan_amd64.deb](http://wielki.tk/vostro/debs/wlan_amd64.deb)

sudo dpkg -i wlan_amd64.deb

first time it will fail then you have to do

sudo apt-get -f install

then it will get all file need to install wlan_amd64.deb

reboot your laptop

all done[/INDENT]

after you set up your networking then you tweak to make battery life extend  longer

[http://andri.andriani.web.id/dell-inspiron-5420-on-ubuntu/](http://andri.andriani.web.id/dell-inspiron-5420-on-ubuntu/)

[INDENT]First what you have to do is install bumblebee not that transformer bumblebee but [this]("http://bumblebee-project.org/"),

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get install bumblebee bumblebee-nvidia
Then you have to set up acpi_call, you can follow how to implement itu from [here]("http://hybrid-graphics-linux.tuxfamily.org/index.php?title=Acpi_call")

after you finish set up then reboot[/INDENT]

I hope it will help you with inspiron 5420, if you have another solution please share with us

Thank you

---

### Post by dpkg on 2012-11-06
Thanks!! I watned to move long time but didnt because of that!
:]]

---

### Post by Milind Bhide on 2012-11-18
Hello dear,

It worked for me, thanks alot..

Regards
Milind

---

### Post by andriansah on 2012-11-18
glad i can help

---

