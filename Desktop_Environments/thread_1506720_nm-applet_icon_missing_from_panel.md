---
title: "nm-applet icon missing from panel"
date: 2010-06-10
forum: Desktop Environments
---

### Post by fivebells on 2010-06-10
The nm-applet icon is missing from the panel.  Right-clicking on System->Preferences->Network Connections, then adding that to the panel gives a workaround, but it's not nearly as informative or easy to use.  The command "killall nm-applet && nm-applet &" runs without error, but does not restore the icon.  Calling "[nm-applet --sm-disable]("http://practicalswitchtoubuntu.blogspot.com/2009/02/restore-missing-network-manager-applet.html")" doesn't help, either.  The workaround suggested in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/439448/comments/64")  does not restore it, nor do any of the other icons appear confused, so I don't think it's that bug.  This is happening after a reinstall (but /home was unchanged) and is happening with freshly-created accounts.  Any other suggestions?

---

### Post by mikewhatever on 2010-06-10
Try adding the notification area to the panel.

---

### Post by fivebells on 2010-06-10
Thank you; that worked.

---

### Post by Alejandro Nova on 2010-08-12
I got in my hands one system where this didn't worked. For it, restarting the NetworkManager service did work.

$ sudo service network-manager stop
$ sudo service network-manager start

The icon is there, it only doesn't display anything. These commands force the nm-applet icon to update itself.

---

### Post by fmurrieta on 2010-09-03
I had apparently the same problem, I tryed everithigng you've suggested with no luck.

I have a bunch of users in this machine.

I've prevoiusly checked the "Available to all users" checkbox for all the wireless networks I use.

After 2 months I've got my problem solved:
 
All I need to do to fix the missing nm-applet was1.- Login as your first user
[INDENT]2.- Go to Edit Network Connections- 
3.- Select your first network
4.- Click the **Edit** button
5.- Unckeck the "**Available to all users**"
6.- Click **Apply**
7.- Repeat for all connections
8.- Repeat for all users
[/INDENT] Hope thi*s can save you* some time!


Fernando Murrieta

---

### Post by cosmolee on 2010-09-05
Alejandro & Fernando:

I've tried both of your suggestions - neither of them work for me.  I also tried completely uninstalling and re-installing network-manager and network-manager-gnome.  

None of this changed the fact that there is no icon to pick to add to the top Panel.  And running `nm-applet` doesn't cause any graphical configuration screen to come up nor appear on the panel.  

As far as this thread is concerned it should be marked NOT solved.

I continue to try to resolve this...

---

### Post by dsw1007 on 2010-09-08
I also encountered this problem, and troubled me several months, but today I found the solution
so simple, and it works.
I wish it will help you.

Here is the steps :
1 : just right click on your panel.
2 : choose " Add to Panel..."
3 : select " Notification Area" 
4 : add it.
5 : and magic comes.

Try it ! 
God bless you !

---

### Post by Katatawnic on 2010-09-09
[COLOR="DarkOrchid"]Thank you, dsw1007... this did the trick! :)[/COLOR]

---

### Post by oylbin on 2011-05-15
> **fmurrieta said:**
> I had apparently the same problem, I tryed everithigng you've suggested with no luck.

I have a bunch of users in this machine.

I've prevoiusly checked the "Available to all users" checkbox for all the wireless networks I use.

After 2 months I've got my problem solved:
 
All I need to do to fix the missing nm-applet was1.- Login as your first user[INDENT]2.- Go to Edit Network Connections- 
3.- Select your first network
4.- Click the **Edit** button
5.- Unckeck the "**Available to all users**"
6.- Click **Apply**
7.- Repeat for all connections
8.- Repeat for all users
[/INDENT]Hope thi*s can save you* some time!


Fernando Murrieta

many thanks to fmurrieta.
my problem is the same thing, some "**Available to all users**" network made the  nm-applet icon missing. 
I cant see the network in network setting dialog, so I can't Unckeck the "**Available to all users**", but I find the setting config file in /etc/NetworkManager/system-connections/ , I removed all the config file in this directory and reboot, then the nm-applet icon go back. :)

---

### Post by shibu_sawyer on 2011-06-20
> **dsw1007 said:**
> I also encountered this problem, and troubled me several months, but today I found the solution
so simple, and it works.
I wish it will help you.

Here is the steps :
1 : just right click on your panel.
2 : choose " Add to Panel..."
3 : select " Notification Area" 
4 : add it.
5 : and magic comes.

Try it ! 
God bless you !
Thank you,it worked.....

---

### Post by frisket on 2011-06-30
In 11.04 on a Dell Latitude D610 laptop, there are two logins. User1 has sudo privs, User2 does not.

When either user logs in, network-manager picks up on whatever remembered wireless network is available, connects, and the nm icon shows in the panel.

If the other user logs in (via Switch User), the connection persists, but the nm icon does not show in the panel.

Under 11.04 it appears there is no way to put the nm icon back in the panel, even when the connection is set to "available to all users", and even when the user missing the icon is User1 (who has sudo privs).

If control is now switched back to the first user who logged in, the nm icon is still there, and the system is still connected, but if that user logs off (rather than clicking Switch User), the connection is dropped, and when the other user gives their password to resume their session, there is now neither connection nor an icon with which it can be re-established.

This would appear to be a bug, but is there a way to ***FORCE*** the nm icon to appear in the panel? The connection is already set to "available to all users", and doing a networking start does not do anything.

Under 11.04 it appears that there is no way to make any icon appear in the panel if it is not already there.

---

### Post by renchu on 2011-07-01
disregard this message

---

### Post by slotto on 2011-07-21
Awesome. Thanks!

---

### Post by Capetownlad on 2012-07-18
> **shibu_sawyer said:**
> Thank you,it worked.....

Hello buddy
Just found your post here and thought I'd say Hi 'cause we have the same surname!

---

