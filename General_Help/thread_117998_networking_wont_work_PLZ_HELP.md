---
title: "networking wont work PLZ HELP"
date: 2006-01-15
forum: General Help
---

### Post by mike63730 on 2006-01-15
ok heres what im doing i got my pc with ubuntu 5.10 and another pc for the wife with ubuntu on it also i have installed a extra nic card in mine and im using a cat 5 cross over cable over to the wifes and cant get the internet working on hers it wont do anything  has anyone dealt with using a crossover under linux  if so i could use some help 
thanks in advance

---

### Post by Lambert on 2006-01-15
1. The box with the two nics, make sure they are on different nets. If your internet nic is on 192.168.0.x then put your crossover nic on 192.168.1.x
2. Make sure ip_forwarding is on for the internet connected box. You do this by going into /etc/sysctl.conf and uncommenting the second line that looks like this.

# Uncomment the next line to enable packet forwarding for IPv4
net/ipv4/ip_forward=1

3. On the second box make sure it has the same network on it. So if crossover on box one is 192.168.1.2 then make it something like 192.168.1.3 
4. Set up default gw as the cross over nic on the 1st box.

so command line setup on 2nd box would look like this

sudo ifconfig eth0 192.168.1.3 up
sudo route add default gw 192.168.1.2 dev eth0

To do this automatically everytime on boot edit your /etc/network/interfaces file so it looks like this on second box

iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.2
auto eth0

On box one, set up interface file the same except don't use the gateway stanza and change address to 1.2 or whatever networking address you're using.

---

### Post by mike63730 on 2006-01-15
i dont understand were to do all this im new with linux systems  soory?

---

### Post by Lambert on 2006-01-15
Ok,

Go into applications>accesories>terminal, this brings up a terminal to do command line actions.

To open a file in an editor with administrator privledges type this

sudo gedit _______

fill in the blank with the file. So to edit the sysctl.conf file I mention type in this command

sudo gedit /etc/sysctl.conf

remove the # from the line and then save and close the file.

To edit the interfaces file you would do something similar

sudo gedit /etc/network/interfaces

For the other ifconfig and route commands I gave you just type them in  as I wrote them.

You can also look at graphically setting up the interfaces by going to system>administration>networking but you will need to edit the sysctl.conf file by text editor.

There are a couple links in my signature for beginners. You may want to read those or there are other resources that would be good that others can recommend.

---

