---
title: "one custom config for all users"
date: 2008-01-01
forum: Desktop Environments
---

### Post by westwinger on 2008-01-01
I'm recently started on Ubuntu.  I've got my configuration for the desktop, Firefox and OpenOffice just about where I want them.

Now I need to add 20 users with the same configurations.  Is there a single conf  file where I can put all the customized info? 

Alternatively, I could write a script to do each step but in this case, I would need to know where each conf file resides.  Rather than open every conf file perhaps someone has done this already.

Another idea was to look in my own user file for the custom conf files and then create a login script which would copy my configuration.  But even in my user file the configuration files are daunting.

Perhaps there is a GUI which does this which I am not aware of.

---

### Post by TVMA on 2008-01-01
So you want to create 20 different accounts, but each of them to have the same configuraiton settings that you have set for your user account?

---

### Post by mcduck on 2008-01-02
Copy all the setting files for programs & desktop into /etc/skel/. When creating new users all the contents in /etc/skel/ are copied into their home directories.

If you need to manage many different desktop setups for many users Sabayon (not the distro but the desktop configuration tool) is a nice one. And then add Pessulus if you need to restrict what those accounts can do..

---

### Post by westwinger on 2008-01-03
"Copy all the setting files for programs & desktop into /etc/skel/. When creating new users all the contents in /etc/skel/ are copied into their home directories."

Thanks, that's a beginning and raises another question:
Do I have to hunt around in my user files for all the applicable configuration files one by one - has this been done before and explained somewhere? - or should I merely copy my entire userfile to /etc/skel ?

---

### Post by p_quarles on 2008-01-03
The configuration files are the ones in your /home directory beginning with "." These can be a bit tricky to copy, so you'll have to use a carefully prepared regular expression to do this in one sweep. This will do the trick:
```
sudo cp -r /home/*username*/.[a-zA-Z0-9]* /etc/skel
```
The letters and numbers in the brackets are there to indicate that the cp command should only copy things beginning with a "." *and followed by* a letter or a number. The "*" indicates that the third and following characters can be anything. 

This is important, because if you omit the [a-zA-Z0-9], it will copy the ".." file, which is a link back to the parent directory. If you did that, you would actually be copying your entire filesystem into the /etc/skel directory, which you certainly don't want to do.

---

### Post by westwinger on 2008-01-03
Thanks.  I _just knew_ there was a simple way to do this and you have given it to me.

---

### Post by oomingmak on 2008-01-04
Won't copying the *entire* home folder mean that private user data (such as cached Firefox passwords etc.) will be made available to everyone? :confused: 

or does it not work like that?

---

### Post by mcduck on 2008-01-04
Yes, it does.

Only those setting files you actually want new users to have should be copied to /etc/skel/. Copying every file from your home would give new users exactly the same settings that you have (including, for example, your browsing history & saved passwords in Firefox).

Perhaps the best way would be to create one new user, configure it exactly the way you want all those new users accounts to be, and then copy _that_ user's home directory into /etc/skel/. This way you wouldn't be copying all your personal settings but instead only those exact files that do the changes you want..

---

### Post by tampagault on 2008-01-12
So, being a complete idiot and relatively new to this, I decided to take the advice posted on this thread. After configuring a user the way I wanted all users to be configured, I sudoed up a root based nautilus session and copied all of the contents of the Home folder (of the correctly configured user) and popped them into the etc/skel directory. The result:

**TOTAL HOSING**

Guys, seriously, I know I'm new to this, and I should have read a lot more before trying it, but didn't anyone think to mention that the user permissions on a simple copy / paste would completely hose up etc/skel? I ended up deleting everything in skel because, well, all the things I had copied over remained under the ownership of the original user account with the wrong permissions to boot. Yep, I know I can use chown / chmod to change the permissions and ownership, but there we're getting into much more complex waters. 

Not meant as an insult guys. It's just an OS and I'm just tinkering around; no harm done. But does anyone have a more detailed answer to this problem? Obviously just copying the home directory (in its entirety or just the config parts) isn't going to get the job done. 

Isn't there some way to set default user setups? How about default group setups? 

Sigh. While we're at it, how do I reset the contents of etc/skel to the original installation setup ;) Cuz that's flushed.

Sigh.

---

### Post by mcduck on 2008-01-12
You should have only copied the setting files you need. And afterwards just chowned them to root. 

Anyway, to get the /etc/skel back to how it was in first place,  I'll attach a package with the original files in case overwrited them.

In my first post I mentioned the GUI tool for this kind of tasks, Sabayon. If you find it hard to select only the setting files you need and to chown them to root, try with Sabayon instead.

---

### Post by tampagault on 2008-01-12
Hey there,

Thanks for the fast reply, and thanks you -very- much for the files.

I tried sabayon but it crashes as soon as I click the Edit button after creating a profile. I noticed on their site that a few people are having the same problem, so it looks like I am out of luck. 

I've done heavy customization to the user account I want to copy, which makes it hard to know what I need to put in etc/skel

For instance, I've gotten rid of the taskbar menus and replaced them with the Ubuntu Main menu, and I've also installed cairo dock, and am using icons I ripped off of gOS (this is going to be a web app box, old thing). I've put the icons into the share directory, and I'm guessing I can put the wallpaper there too. As for everything else, I have no idea. How can I manage that without Sabayon? 

I may be biting off more than I can chew here. I'm actually not completely certain what the read / write permissions should be once stuff goes into skel. I'm guessing that users only need read since the files are getting pulled into their home directories? Or do I need to make them read/write right off the bat? 

'Tis very confusing for this noob. :confused:

Also, fyi, it looks like there's work to combine Sabayon with the lock down software you mentioned. Should be a good combo.

I mean, I'm guessing it will be since I can't get Sabayon to work and so don't know if it is any good. 

Related problem: I can't seem to get any visual effects from compiz to work in any user account except for the primary account. Very odd.

Anyhow, I'm stuck. Any help: Much Appreciated!

:popcorn:

---

### Post by tampagault on 2008-01-12
Anyone?

---

### Post by p_quarles on 2008-01-12
Well, as mcduck mentioned, you should only need to change the owner of the config files to root. The permissions don't need to be fiddled with. If you're using Gnome, virtually all of your settings will be in ~/.gconf. Compiz settings will be in ~/.config/compiz. Basically, you'll have to identify what apps you've modified, and then find their configuration folder. Any changes (except for those made as root) will be stored in some folder in the home directory.

---

### Post by tampagault on 2008-01-13
Actually, I'm trying to use Sabayon now...

I mentioned before that it crashed, so since I wasn't far along in my work I just reinstalled ubuntu gutsy. This time, Sabayon worked (though it does crash and is quite slow).

In Sabayon :confused:I created the custom profile that I want to apply to all users, and in Sabayon I specified what users should use the new custom profile, but when I log into said user accounts the default ubuntu configuration shows up, not the custom one I created.

Is there something I'm missing? Do I have to do something to make the configurations take? Are there permissions issues?

McDuck, am I doing something wrong here?

This all seems pretty difficult. The quest continues.

---

### Post by westwinger on 2008-02-27
I opened this thread but haven't been back in a while because the suggestion of copying my hidden files to /etc/skel DID NOT WORK.  

The "cp -r" command does not copy recursively in /etc/skel as it does elsewhere.   I've just found some time to play around with this again and I have found that reversing the process works fine, i.e. cd down to /etc/skel and then, for instance

sudo cp -r /home/myusername/.openoffice.org2/user .openoffice.org2

Of course, earlier warnings apply:  don't put anything in here you don't want all the new users to see.

---

