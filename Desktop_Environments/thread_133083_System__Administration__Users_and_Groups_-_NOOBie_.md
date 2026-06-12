---
title: "System / Administration / Users and Groups - NOOBie BOOBOO"
date: 2006-02-19
forum: Desktop Environments
---

### Post by cellarguy on 2006-02-19
A little bit of knowledge is dangerous, as they say.

Installed Ubuntu yesterday and was immensely pleased with how it found all my hardware and it updated seamlessly.  Thank you!

Previously tried some linux packages - Slackware, Redhat, even Debian (Potato).  So I was one of those 'dangerous' users.  I thought I knew that I needed to add another user to avoid running as *root*.  Little did I know that Ubuntu sidesteps this problem: there is no default root access.

I tried fiddling with the **Users and Groups** settings.

I have to complain about the documentation for this little gnome program.  Somebody obviously thought it was so simple any idiot could figure it out.  Obviously, they had not taken into account the extent of my brain failure.

Oh, I tried to use **HELP** before mindlessly tweaking.  The **HELP** was totally inadequate.  Is a checkbox on when it looks like it is 'up', or when it is 'down'?  Why is there no right-click menu for these checkboxes?  Why can I not see what is underneath the selected line (ie. I can't see what I'm doing)?  Why do I have to select a new line to see what I just did on the last line?  That's bad design.  Too simple for simple folk.

I think I took away all my administrator privileges, in my old user *and* my new user.  **I can't run Users and Groups anymore**.  Or anything else requiring root-ish privileges.  

The up side: now I am* really *safe - especially from myself!  Boy, do I feel secure!

The down side: I'm facing a re-install.

Fortunately, its just a day in the life.

---

### Post by kaamos on 2006-02-19
You don't need to reinstall because of that.

If you open a terminal (Applications->Accessories->Terminal) and type
```
groups
```
does the list contain "admin" ? If not, do this:

Reboot the machine and choose recovery mode in grubs menu. You should get a root shell. Then type
```
adduser *username* admin
```
substitute *username* with your username. Then type
```
shutdown -r now
``` and let ubuntu boot normally. Then try this in a terminal:
```
sudo synaptic
```

If this does not help, post possible errors and the output of "groups" here. Good luck!

---

### Post by cellarguy on 2006-02-19
Thanks, kaamos - 

Always take a shower before reinstalling.
That's what I did.
I even had the cd in the drive, ready to go, 
But, hope springs eternal, and I thought, "check for replies first".

Your first reply didn't work, btw.
But by the time I discovered that, you had edited it to the one above
that *did* work.  Much obliged.

I seem to have my admin privileges back.
I am dangerous again!

---

### Post by kaamos on 2006-02-19
Glad to hear that it worked. I was being an idiot with the first version.. That needed admin priviliges to get admin privilidges. Duh. ;)

---

### Post by tvgm2 on 2006-02-19
How would one go about this if they're using LILO as a boot manager?

---

### Post by Resurrection on 2006-02-20
[QUOTE=kaamos]You don't need to reinstall because of that.

If you open a terminal (Applications->Accessories->Terminal) and type
```
groups
```
does the list contain "admin" ? If not, do this:

Reboot the machine and choose recovery mode in grubs menu. You should get a root shell. Then type
```
adduser *username* admin
```
substitute *username* with your username. Then type
```
shutdown -r now
``` and let ubuntu boot normally. Then try this in a terminal:
```
sudo synaptic
```

If this does not help, post possible errors and the output of "groups" here. Good luck![/QUOTE]
Thank you kaamos, I did the same thing as cellarguy I think.  Your fix above worked great.  

I wonder if this is one of the top 5 lessons that ubuntu users have to learn the hard way.

---

### Post by RAOF on 2006-02-20
[QUOTE=tvgm2]How would one go about this if they're using LILO as a boot manager?[/QUOTE]
You'd want to boot "linux single" from the lilo prompt.  If you don't get a lilo prompt, then... you could fix it with a live cd and chroot.  I **think** that would go something like:
1) Boot live cd
2) Mount / (root) Ubuntu partition
3) sudo su (Get a root prompt)
4) chroot /where_you_mounted_ubuntu_root_partition
5) adduser *username* admin

---

