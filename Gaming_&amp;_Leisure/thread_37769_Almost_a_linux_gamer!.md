---
title: "Almost a linux gamer!"
date: 2005-05-28
forum: Gaming &amp; Leisure
---

### Post by wh33t on 2005-05-28
Hey guys, I get this error message sometimes when I'm playing Enemy Territory.

   Error: unable to write to hunkusage.dat

So i'm pretty sure that is a permissions problem, I'm just not sure what the command is to change the permissions. chmod something right? I'm also not sure what to set the values too.

Also, if anyone else out there plays Enemy Territory could you please comment on how long it takes you to get into a game? My game keeps 'attempting' to download map files and stuff from game servers but nothing ever starts. maybe its cause like my map directory is also in read only permissions... Hrm.

---

### Post by apollyonis on 2005-05-28
```
sudo chmod -R a+rwx ~/.etwolf
```
and if that doesn't give permission, try
```
sudo chmod -R a+rwx /usr/local/games/enemy-territory
```
Once the game starts up, connecting to a server is totally dependant on your connection. Mine connects just fine.

---

### Post by thrift on 2005-05-28
There is a better way to do this.  If you are looking for a more secure way to do this try this instead:

Go to System->Administration->Users and Groups
enter you password when prompted.
Go to the groups tab.
Click the Show all users and groups checkbox.
Find and click the games group.
Once it has highlighted, click properties
Find your username in the left pane and highlight it.
Click add.

Open a terminal and run the following commands:
sudo bash
<enter your password>
chown <your username>:<your username> -R ~/.etwolf
chown root:games -R /usr/local/games/enemy-territory
chmod 750 -R ~/.etwolf
chmod 750 -R /usr/local/games/enemy-territory

You will need to log out completely and back in for this to work.

What we have done is added you to the games group(we needed you to log in and back out due to this).

We have made your local et configuration readable, writable, and executable by you and readable and executable by your group.

We have made et's main program directory readable, writable, and executable only by root and readable and executable by the games group, for which you are a memeber.

Now if you were to have another user for which you would like to give access to play et, but not be able to do anything to it which would mess pu your config, you can just add them to the games group.

Just providing a more secure/proper way to do this.  The way mentioned by apollyonis should allow you to play the game as well, but is not secure.

---

### Post by wh33t on 2005-05-28
Well, actually what I ended up doing was a chmod 777 on the directory, and then in the sub directories.. that didn't seem to help. Still got the hunkusage.dat error. So I was reading up on websites, and its a common problem for anything using the Quake3 engine apparently. Even on windows. So the site just to delete it and I guess the game recreates when it runs again. And so now I can host games. But I still cant seem to connect to any of them. It just seems to attempt to download the files and never actually transfers any data. I think maybe its a firewall issue. I have a linksys router connected, perhaps I need to open some ports up.

---

### Post by thrift on 2005-05-29
ah.  removing ~/.etwolf worked.

You are probably downloading a lot of files and maps because you haven't actually got connected to any servers yet.  The first week or so you play you'll be downloading lots of files when you first connect to a server.  It may be easier to find an ftp site that hosts the files and download them with a high speed connection, burn them to a cd, then copy them to your .etwolf directory.  That will minimize your downloads when trying to play.  No ports need to be open on the firewall for wolfet.

by the way, if you remove the ~/.etwolf directory in the future you will lose all these maps and mods you downloaded and have to download them again later.  It may be usefull to make backup copys of this directory if you experience frequent problems with it.

If you can't downloading anything and just want to play, try looking for a server that just plays the classic maps with no mods, or that just plays a single classic map.  Then you may only have to download a clan graphic and maybe etpro or shrubet.

Hope that helps.  Good Luck.

---

### Post by wh33t on 2005-05-29
That does help thanks.

---

