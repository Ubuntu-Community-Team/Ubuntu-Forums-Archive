---
title: "File sharing in ubuntu &amp; windows"
date: 2009-06-02
forum: General Help
---

### Post by pramathesh on 2009-06-02
Guys I've recently formatted my desktop to Vista and I'm presently using a netgear DG834G. On my laptop I'm running Jaunty. Everything required for sharing has been put up on vista but when I go to network in Ubuntu it shows WORKGROUP and it tries to fetch the share list but fails. Is there something that I'm missing here?

---

### Post by pramathesh on 2009-06-02
:o

---

### Post by gawadelnil2002 on 2009-06-02
> **pramathesh said:**
> Guys I've recently formatted my desktop to Vista and I'm presently using a netgear DG834G. On my laptop I'm running Jaunty. Everything required for sharing has been put up on vista but when I go to network in Ubuntu it shows WORKGROUP and it tries to fetch the share list but fails. Is there something that I'm missing here?
Are u working on net using dhcp???

---

### Post by gawadelnil2002 on 2009-06-02
well if u r working on dhcp u need to change to static ip first and u can do that by going to network manager in try icon and right click on it and then choice edit connection a window will appear contains some tabs under wired tab click add and it will open another window asking u about ur network information, there in this window u will find three tabs , the first tab called wired too, all what u have to do in this tab is writing ur mac adress, wait i know u cant keep that adress in ur mind so u have to go the edit connections tab teh first window we opened and click on eth 0 connection there it will ask u a password and then it will open u will find ur mac adress there u can copy it for the window of new connection we working on it , after writing ur mac adress in teh first tab go to the last tab that is called ipv4 setting this tab will contain ur information about the network , like the computer ip adress the domain u will work on it and the dns ip , so go there and change it form automatic dhcp to , mannual and start to add the information of ur computer first ur ip adress second ur net mask thirs the gateway ip and go to dns ip write urs there , now there is one thing lift, that u have to write in domain search box , u will write there lan
together again
method==               mannual
adress                ==ur ip adress   ex: 10.0.0.157
netmask==             ur net mask   ex:255.0.0.0
gateway             ==ur router gateway 
search domain==    lan
dns server==          ur dns ip

now u can go to network form places menu and network will open and choice windows network and after that choice ur netwoork group name and everything will work , now u can see the other windows computers on ur network 

note:with this method u can see any windows computer on the network but the windows computer cannot see u and if u want windows computer to see u it another topic and i didnt try it yet

---

### Post by pramathesh on 2009-06-02
I'm on DHCP but I've made sure that my laptop gets the ip of 254.11 and desktop gets 254.10. Is that going to help in any case? Laptop BTW is wireless and desktop is wired to the modem/router

---

### Post by pramathesh on 2009-06-02
I've come across this samba thingy is this what I'm missing in my case? All I want to do is be able to see, create and edit files from Laptop (Ubuntu) to Desktop (Vista). Doesn't matter if Desktop doesn't get access to the laptop.....

---

### Post by pramathesh on 2009-06-02
**Unable to mount location**
Failed to retreive share list from the server


This is the exact error message

---

### Post by lisati on 2009-06-02
> **pramathesh said:**
> I've come across this samba thingy is this what I'm missing in my case? All I want to do is be able to see, create and edit files from Laptop (Ubuntu) to Desktop (Vista). Doesn't matter if Desktop doesn't get access to the laptop.....

Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by pramathesh on 2009-06-02
That article is pretty self exlpnatory hope I do get it right. But how I'm I supposed to get the NETBIOS name of my computer!? I think this is to do with the Vista computer....

---

### Post by lisati on 2009-06-02
> **pramathesh said:**
> That article is pretty self exlpnatory hope I do get it right. But how I'm I supposed to get the NETBIOS name of my computer!? I think this is to do with the Vista computer....

I think in Vista it's called "Computer name" or some such term. 
When setting up the samba part on Ubuntu you can choose anything you like.

EDIT: In Vista you can click on Start->Network and it will show the NETBIOS names of the computers it recognises. In Ubuntu, it's what shows between the "@" and the "$" on the command line prompt.

---

### Post by pramathesh on 2009-06-02
I've folllowed this 
[b]1. Find out the 'Workgroup' your windows computer(s) are on

    a. Right click computer on start menu (vista) or my computer (xp) and select properties

    b. Workgroup is listed in section 'Computer name, domain, and workgroup settings'

2. Install samba on ubuntu, sudo apt-get install samba
3. Edit smb.conf to reflect your proper workgroup name found on windows machine, restart samba

    a. gksudo gedit /etc/samba/smb.conf

    b. sudo /etc/init.d/samba restart

4. Create a samba user and password

    a. sudo smbpasswd -a <YOUR_USERNAME>

    b. this will prompt you to create a pasword for the user


Your computer should be recognized on the network now, use your windows login credentials to access windows shares, and your smbpasswd login info you created for windows-to-linux connections.

In nautilus (file browser) you can easily right click the folder and select 'Sharing options' granted you have the correct file permissions for the folder you wish to share. Anything under the home directory should be easily shared. When you create your first shared file it may prompt to install packages required for sharing, make sure you follow through.[/b]

Mentioned by mattgyver83
over [here]("http://ubuntuforums.org/showthread.php?t=1151752")
as of now I see ROAD-RUNNER in my network but still the same error persists i.e **Failed to retreive share list from server**

---

### Post by pramathesh on 2009-06-02
:o

---

### Post by 3rdalbum on 2009-06-02
You need to make sure that your share's permissions are set to read and write by all users, or specifically by a Samba user account that has the same name as the client's user account. Your users need to have Unix user accounts AND Samba user accounts.

If your server is Ubuntu, then you can install the "system-config-samba" package which makes it easy for you to create new Samba users and change the properties of shares.

---

### Post by pramathesh on 2009-06-03
I've put nothing to share from Ubuntu all I want to do is copy paste stuff from my laptop to the desktop. Samba has got the same username password as my laptop. Windows share has rights to read, write and execute. I can see print share too. But then there's no printer here. Why can't I see the files that I've put to share from windows. In fact all my drives have been shared including windows C: too.

---

### Post by dmizer on 2009-06-03
See the 6th link in my sig.

---

### Post by pramathesh on 2009-06-03
Wow this link of yours Mr. Dmizer brot me a step closer I can now see the drives I've shared asa again it is so close yet so far. I see drives with a $ behind it and w/o a $ behind it. If I hit the drive with $ behind it, it asks for a password, which I don't have (assuming it is asking for windows credentials). The windows account name is Administrator. If I happen to hit the drive without the $ sign it tells failed to mount windows share. Attaching an image hope it helps.
[[IMG]http://img36.imageshack.us/img36/9885/screenshotgjo.th.png[/IMG]](http://img36.imageshack.us/my.php?image=screenshotgjo.png)

---

### Post by dmizer on 2009-06-03
If your trying to connect to Vista, you will not be able to connect to any UAC protected drive/directory. Because of this, sharing the entire drives will not give you access (unlike it did in XP). Believe me when I say ... this is a very good thing. You don't want your entire system hanging out there for all to see.

Share from a folder instead. For example, are you able to browse through the "Public" folder? More information here: [http://www.vistax64.com/vista-security/103790-access-denied.html](http://www.vistax64.com/vista-security/103790-access-denied.html)

---

### Post by pramathesh on 2009-06-03
Yes I was earlier able to see the public folders. So in other words Mr. Dmizer is it not possible in any ways to browse my partitioned drives? Which in my case is D:, E:, F:, G:. I'm on the Administrator a/c plus it's a slipstreamed version of Vista I think I've removed the UAC before installation. But in any case I don't see that popping up on me since I'm on the Administrator a/c. Won't this be of any help!?

---

### Post by pramathesh on 2009-06-03
I think  we need to work my the Vista machine now. I don't think Ubuntu is being a pain in the butt now. But I wonder what to do with it. May be hit Henrry Gates with it..... :rofl:

---

### Post by pramathesh on 2009-06-03
In public folder I can't paste anything from my laptop =((

---

### Post by pramathesh on 2009-06-03
Sharing the folder works just fine. Can't we just do something for the drives? Thanks a million times Mr. Dmizer, if only I knew your real name! :)

---

### Post by dmizer on 2009-06-03
People call me dmizer in real life :-D. The "mr." isn't necessary ;)

I think the problem your experiencing is actually a good thing. Security wise, it's terrible to share entire drives. You're much better off dedicating single folders to file shares. If you want an entire drive to be dedicated to sharing, then share the first folder on the drive and put everything else inside it like so:

D:/ddrive-shared/Music
D:/ddrive-shared/Movies
D:/ddrive-shared/Pictures
D:/ddrive-shared/Documents
D:/ddrive-shared/Other
etc

Then you can share the "ddrive-shared" folder and all it's contents.

---

### Post by pramathesh on 2009-06-04
Yes will surely take a note of it. Thanks a zillion times for the help you've provided. Let me know if there is annything else that I should take into account here.

---

### Post by dmizer on 2009-06-04
> **pramathesh said:**
> Yes will surely take a note of it. Thanks a zillion times for the help you've provided. Let me know if there is annything else that I should take into account here.

I have no idea what else you should take into account as I don't even own a Windows computer ;)

Glad we got things going for you though.

---

### Post by pramathesh on 2009-06-04
I would haved chucked windows too. But just that I can't get the gaming bug out of me. One more thing I'd like to ask here is, is it possible to auto mount all the network drives on the desktop rather then me having to click in network and do all the thingy manually....

---

### Post by dmizer on 2009-06-04
> **pramathesh said:**
> I would haved chucked windows too. But just that I can't get the gaming bug out of me. One more thing I'd like to ask here is, is it possible to auto mount all the network drives on the desktop rather then me having to click in network and do all the thingy manually....

I don't recall (I don't use Gnome). There's probably a "send to" link available upon right clicking on the folders.

Alternatively, you could hard mount them in fstab and they would automatically appear and disappear when available/unavailable. If you'd like to look into making that work, please see the 2nd link in my sig.

It's more work, but the rewards are worth it.

---

