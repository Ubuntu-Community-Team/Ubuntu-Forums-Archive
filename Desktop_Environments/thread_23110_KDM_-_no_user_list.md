---
title: "KDM - no user list"
date: 2005-03-31
forum: Desktop Environments
---

### Post by m29389 on 2005-03-31
Hello

I installed kubuntu a few days back and it's looking good so far.

My one problem is that at the kdm login screen there is no user list. I have tried all the different options in the login manager section of the control centre but I cannot seem to add this feature. The settings for a list are all still there but they do nothing.

Having had a quick search around the place I have got the impression that this is because the new version of kdm in kde 3.4 (or maybe in an earlier version too) no longer provides a list of users.With passwordless logins you used to be able to simply double-click on the user's icon to login and I am frustrated that this functionality no longer exists. Being very lazy I don't want to have to type in user names  ;) 

Perhaps somebody knows if this is a change in the new kdm or just some sort of theme issue. Is there a way to get the old functionality back? This seems like a backward step to me...

thanks

---

### Post by lao_V on 2005-03-31
In kde 3.4 you now have themed kdm. This could have resulted in the disappearance of the user's list. Have you tried a theme that supports/displays user's list??

---

### Post by m29389 on 2005-03-31
Thanks for the reply.

I looked a little harder at kdm themes and have tried two themes which have user lists from kdelook.org. I think they are both gdm themes (I hadn't realised kdm supports gdm themes) but neither work.  I get an error message,
"Theme not usable with authentication method 'Username + password (classic)'",
I click "ok" (the only option) and am then taken to a login prompt which is a bit mangled and does not work.  There is only a box where the the user list should be anyway.

Next I edited a copy of the kubuntu's theme xml file with these lines from one of the gdm themes:

<item type="rect">
 <normal color="#000000" alpha="0.0"/>
  <pos anchor="n" x="50%" height="548" width="438"/>
   <fixed>
    <item type="list" id="userlist">
     <pos anchor="nw" x="1" y="1" height="-2" width="-2"/>
    </item>
   </fixed>
  </item>
 </box>
</item>

This gives me the kubuntu theme (working fine) with a nice translucent box with nothing in it... I don't have a clue what I am doing in the theme's xml file but they seem fairly straight forward.

I can only assume that kdm does not support the user list (anyone know for sure??) but if anyone knows of a kdm theme with a user list that works then please post a link.  Or if you know what should be in the xml file please also let me know.

thanks

---

### Post by freelsjd on 2005-03-31
I am having this same problem. With kde3.2 and earlier, I had kdm set up for a multi-user machine with a user list and adjacent pictures of the individuals so they would just click their picture and login. Now with my new kubuntu kdm interface, all I have is a login box. There must be a way to do this.:-k

---

### Post by aramazan on 2005-03-31
[QUOTE=m29389]My one problem is that at the kdm login screen there is no user list.[/QUOTE]
I've installed Kubuntu preview and the user list is there, by default. Any chance that you have installed kde-core on top of Canonical Ubuntu? If so, as per [http://www.ubuntulinux.org/wiki/InstallingKDE](http://www.ubuntulinux.org/wiki/InstallingKDE) you're advised to install either kubuntu-desktop or kde-core plus kubuntu-default-settings packages, in order to get Kubuntu specific tweaks.

---

### Post by freelsjd on 2005-03-31
In my case, I installed Ubuntu, then installed kubuntu-desktop on top of that.  The kubuntu-default-settings package is installed, but the kde-core is not.

---

### Post by m29389 on 2005-03-31
I installed using the kubuntu preview cd and have since done a fresh install with the kubuntu release candidate cd.  KDM has the kubuntu wallpaper so I am presuming that I have the kubuntu kdm theme.  I have also tried uninstalling and reinstalling kubuntu-desktop, kde-core and kubuntu-default-settings in various combinations...  no user list...

maybe I will try using gdm instead!

---

### Post by aramazan on 2005-04-02
[QUOTE=m29389]I installed using the kubuntu preview cd and have since done a fresh install with the kubuntu release candidate cd.  KDM has the kubuntu wallpaper so I am presuming that I have the kubuntu kdm theme.  I have also tried uninstalling and reinstalling kubuntu-desktop, kde-core and kubuntu-default-settings in various combinations...  no user list...[/QUOTE]
Strange, but I experience the same problem with Kubuntu-RC. Now I'm not that sure whether user list was showing on default Kubuntu-Preview install or I had done some tweaking that caused it to show as a side effect. Anyway, it's missing in default Kubuntu-RC install (kcontrol entry for displaying user list is already enabled by default). Reported it to kubuntu-users list.

---

### Post by finster on 2005-04-18
[QUOTE=aramazan]Strange, but I experience the same problem with Kubuntu-RC. Now I'm not that sure whether user list was showing on default Kubuntu-Preview install or I had done some tweaking that caused it to show as a side effect. Anyway, it's missing in default Kubuntu-RC install (kcontrol entry for displaying user list is already enabled by default). Reported it to kubuntu-users list.[/QUOTE]
 I'm experiencing the same problem - can't seem to get a list of users on the login screen - I have to type them into a text box.

I've tried various different things with no luck. Anybody else have any ideas?

---

### Post by windymiller on 2005-04-18
[QUOTE=finster]I'm experiencing the same problem - can't seem to get a list of users on the login screen - I have to type them into a text box.

I've tried various different things with no luck. Anybody else have any ideas?[/QUOTE]
 you need to edit /etc/kde/kdm/kdmrc and find the line:

UseTheme = true

and change to:

UseTheme = false

You can then use Control Centre to turn the user list on.

---

### Post by m29389 on 2005-04-28
thanks

I'm away from my computer at the minute so when I get back I will give it a try...

---

### Post by jobezone on 2005-05-16
> you need to edit /etc/kde/kdm/kdmrc and find the line
In my system (Ubuntu plus KDE) it's:

/etc/kde3/kdm/kdmrc

---

### Post by ChodeNode on 2005-09-13
I have this problem as well. I tried setting that value to False and it definitely did change the login window, but still, I have no username list. Anybody else have further ideas?

---

### Post by daller on 2005-09-14
It works for me now! (setting UseTheme=false)

Do you have a link to a great theme on [http://www.kde-look.org?](http://www.kde-look.org?)

...the standard theme is ugly!

---

### Post by Cimmo on 2006-11-23
the problem is kdm WITH theme doesn't support users list like GDM, so the only mode is to put false the useTheme, but making this results in no Theme!

This is fixed but only for KDE 4.0 :(

---

### Post by daller on 2006-11-23
Well, I can wait!

Great to hear that this will be implemented!

Do you know if it will be the default setting?

KDE 4.0 is going to kick ***!

---

### Post by Cimmo on 2006-11-23
> **daller said:**
> Well, I can wait!

Great to hear that this will be implemented!

Do you know if it will be the default setting?

KDE 4.0 is going to kick ***!

I think will be like GDM where you have or not users list depending the theme you choose.
But I'm not sure...

---

### Post by Ateo on 2007-05-17
> **Cimmo said:**
> the problem is kdm WITH theme doesn't support users list like GDM, so the only mode is to put false the useTheme, but making this results in no Theme!

This is fixed but only for KDE 4.0 :(

Please, before you start spreading misinformation, make sure you are certain about your claim.

The reason there is no user list on KDE themes, by default, is because Ubuntu variants don't put newly created users into the 'users' group. Therefore, you NEED TO ENABLE the user that you want displayed in the KDM userlist.

Kcontrol -> System Administration -> Login Manager -> Users

In there, you need to have 'Shows List' checked and 'Inversion selection' unchecked. Then add the user group you wish to permit to be displayed.

What I do is I just add all new users to the 'users' group and allow the 'users' group to be displayed in KDM.

Addtionally, you only need the packages that kubuntu-desktop pulled in. No additional stuff required.

HTH.

PS: You can replace the 'users' group with any group you want.

---

### Post by Cimmo on 2007-05-17
> **Ateo said:**
> Please, before you start spreading misinformation, make sure you are certain about your claim.
or probably you can start to be calm and read that your method works only if you turn off theme in kdmrc as I said.

Tried it and doesn't work as expected with theme on!
And yes I have added "users" group to two real users, and yes added reverse list, and yes checked show list and yes checked the two users in kdm->users and NO it doesn't work.

---

### Post by Ateo on 2007-05-17
> **Cimmo said:**
> or probably you can start to be calm and read that your method works only if you turn off theme in kdmrc as I said.

Tried it and doesn't work as expected with theme on!
And yes I have added "users" group to two real users, and yes added reverse list, and yes checked show list and yes checked the two users in kdm->users and NO it doesn't work.

See the word please? That should indicate that I am calm. Why would I stress? I am just saying you are wrong and to be sure to not spread misinformation. I hate to inform you but you are mis-configuring KDM and that is why you aren't seeing users in the userlist.

I have theme turned on (in kdmrc). I also added my users to the 'users' group and allow users in the kdm userlist to be displayed. It works (in kde 3.x). I don't know where you got the idea that it doesn't.....

When you turn theme off in kdmrc, it displays the default login screen, which, by the way, also has the ability to display a userlist. =) You just have to configure it correctly.

Now, I'm not sure about this but I do believe users must have a photo assigned to them to be displayed. I could be wrong though...

---

### Post by Cimmo on 2007-05-17
> **Ateo said:**
> 
Now, I'm not sure about this but I do believe users must have a photo assigned to them to be displayed. I could be wrong though...

so you are saying that in your /etc/kde3/kdm/kdmrc there is this line:
UseTheme=true

do you confirm?

If yes which theme are you using?

---

### Post by Ateo on 2007-05-17
> **Cimmo said:**
> so you are saying that in your /etc/kde3/kdm/kdmrc there is this line:
UseTheme=true

do you confirm?

If yes which theme are you using?

Yes. I am saying that. I originally changed it to false and didn't like the generic login window. So I changed it back determined to figure out how to get my userlist. You see, I've been using KDE for a very long time and know it very very well and had it set many times before so I knew it could be done, I just couldn't remember the exact thing to do since it's not often I need to reinstall or revert to a backup.

The reason why I was fighting with this userlist thing is because I created my own kdm login screen which has a userlist and i wanted my userlist. So, the theme is mine... But any theme with a userlist will work.

---

### Post by Ateo on 2007-05-17
From Chapter 4, Configuring KDM - KDE Help Center

> Users
From here you can change the way users are represented in the login window.
You may disable the user list in kdm entirely in the Show Users section. You can choose from:

Show List

Only show users you have specifically enabled in the list alongside If you do not check this box, no list will be shown. This is the most secure setting, since an attacker would then have to guess a valid login name as well as a password. It's also the preferred option if you have more than a handful of users to list, or the list itself would become unwieldy.

Inverse selection

Allows you to intead select a list of users that should not be shown, and all other users will be listed.
Independently of the users you specify by name, you can use the System UIDs to specify a range of valid UIDs that are shown in the list. By default user id's under 1000, which are often system or daemon users, and user id's over 65000, are not shown.

You can also enable the Sort users checkbox, to have the user list sorted alphabetically. If this is disabled, users will appear in the order they are listed in the password file. kdm will also autocomplete user names if you enable the Autocompletion option.

If you choose to show users, then the login window will show images (which you select), of a list of users. When someone is ready to login, they may select their user name/image, enter their password, and they are granted access.

If you permit a user image, then you can configure the source for those images.

You can configure the admin picture here, for each user on the system. Depending on the order selected above, users may be able to override your selection.

If you choose not to show users, then the login window will be more traditional. Users will need to type their username and password to gain entrance. This is the preferred way if you have many users on this terminal.

---

### Post by Cimmo on 2007-05-17
> **Ateo said:**
> 
The reason why I was fighting with this userlist thing is because I created my own kdm login screen which has a userlist and i wanted my userlist. So, the theme is mine... But any theme with a userlist will work.
I repeat that here with kubuntu 7.04 default theme, DOESN'T WORK!

---

### Post by Ateo on 2007-05-17
> **Cimmo said:**
> I repeat that here with kubuntu 7.04 default theme, DOESN'T WORK!

So, um. Get another theme? You're not restricted to the default themes you know. Also, I don't remember any of the default themes having userlists. You need to get a theme that has a userlist.

This is a clone of the kubunut default except with a userlist -> [http://www.kde-look.org/content/show.php/Kubuntu+Feisty+UserList++?content=56914](http://www.kde-look.org/content/show.php/Kubuntu+Feisty+UserList++?content=56914)

---

### Post by Cimmo on 2007-05-17
> **Ateo said:**
> So, um. Get another theme? You're not restricted to the default themes you know. Also, I don't remember any of the default themes having userlists. You need to get a theme that has a userlist.

This is a clone of the kubunut default except with a userlist -> [http://www.kde-look.org/content/show.php/Kubuntu+Feisty+UserList++?content=56914](http://www.kde-look.org/content/show.php/Kubuntu+Feisty+UserList++?content=56914)

when someone is right I always change my opinion.
You are right!

With that theme it worked!
Anyway we are here all to improve so there is no need to "attack" someone, I claimed before that isn't possible because a lot of people tried and didn't worked, I also tried in the past a lot of themes, probably all were with users list off, don't know.

---

### Post by Ateo on 2007-05-17
dude. i just want you to understand that there was no 'attack'... don't be so sensitive. I just made a request of you. I even said please (my first word)... =)

> **Cimmo said:**
> when someone is right I always change my opinion.
You are right!

Me too!!! That's how we learn.

Anyways, glad you got it working....

Cheers.

---

### Post by Cimmo on 2007-05-17
> **Ateo said:**
> dude. i just want you to understand that there was no 'attack'... don't be so sensitive. I just made a request of you. I even said please (my first word)... =)
you have started thread like "I know something that others don't know and want to highlights this at all costs!"

read again your first post and read with this "key".
Anyway I'm ok and now with users list.

bye

---

