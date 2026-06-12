---
title: "Help requested on various issues !"
date: 2007-05-07
forum: Desktop Environments
---

### Post by atomcreator on 2007-05-07
Hi,
We are a charity youth organisation and have had 2 pc's donated with Ubuntu 6.10 installed on them. We would like to use them in our ' lounge ' area for internet browsing only. I am fairly proficient with windows but have no experience with Ubuntu, although it looks nice and clean. We have very little money to convert them to windows machines though, so I would like to try Ubuntu.

I have a few questions -
Firstly I will need to network these computers to the existing windows pc's but I guess I can find out more about that browsing the relevant areas of this forum - we have a standard P2P Win network - unless some kind soul could provide me with a link ( I'm short of time ! )

Secondly, we would like to lock down each computer to only allow internet access ( as in an internet cafe ) - how do you do that ?

Next, I am aware of a pretty good program for windows called Naomi, which is a very good free parental control type software - could anyone tell me if it is compatable with this ? Or if not ( I know its a long shot ), then what could I use to stop inapproprate sites being accessed by the kids ?

And lastly, is there a way of including a ' logout timer ' if the machine is unused for 5 minutes for example ?

Many thanks for any help or replies in advance,

Mark

---

### Post by atomcreator on 2007-05-07
can anyone help ? or have I posted in the wrong area ?

---

### Post by enopepsoo on 2007-05-07
I know that the Ubuntu CE must come with a web filter installed.  I am sure you could find one if you did a search in the Synaptic Package manager.

So far as having them just having internet access, that should be pretty well configured from the get go, as there should not be any services running on the machines, and the firewall should only be open on 80 and 443 by default (as far as I remember, probably 25 and 110 are open too though).

I don't know what you would use to log people out after 5 minutes.  You could probably write a bash script that would do it fairly easily, but that is not something I know how to do.:confused:

**note:**  I find it is a lot easier to get answers if you ask one question at a time.

---

### Post by JawsThemeSwimming428 on 2007-05-07
What type of PC's do you have Ubuntu running on? Does your network have a router or a wireless router in it?

---

### Post by Praill on 2007-05-07
What you need is to setup user permissions. Basically any file you dont want them to access change its owner to 'root' (right-click-->properties-->permissions-tab or chown in a terminal) and never give out the root password. This should almost be done for you as anything outside of /home/user is generally owned by root. Then remove all items (but the neccessary ones) from the panel menu for the pertinent user by right clicking it and  selecting menu editor.
To prevent users from adding items to the panel menu and such most admins just disable right clicking for all users but root. How you do this in ubuntu I must confess I dont know. But as the above user suggested, I would ask that single question in a new thread and you should get a response (it cant be that hard, its got to be in X config).

Other than that you should be good. Ubuntu is set up so that doing anything important requires a root password.

*Edit: oh and as for the parental filters I have no idea. Sorry :( I like my browsers wide open :)*

---

### Post by Opsidian on 2007-05-07
You can setup a user login, even make it the auto login, and just keep that login from having root access. I have 15 stations setup in our youth facility and this has kept anyone from trying to add or change anything for the past year.

Allowing internet time, well i am stumped on that one.

Check this forum for parental controls, some good links there.
[http://ubuntuforums.org/showthread.php?t=232884&highlight=parental+filters](http://ubuntuforums.org/showthread.php?t=232884&highlight=parental+filters)

Where are you located? Check for a LoCoTeam near you, they might be able to help you with some hands on training or give some suggestions as well. 
[https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

Hope this helps

---

