---
title: "Could not update ICEauthority file"
date: 2014-03-07
forum: Desktop Environments
---

### Post by jrmchess on 2014-03-07
I have kubuntu low fat on ubuntu 12.04. I changed my username using the "users" app in the kde desktop but after rebooting when I log in I get the error > Could not update ICEauthority file /home/<new username>/.ICEauthority What should I do? I am a novice linux user so would request u to please explain things in detail... Thanks

---

### Post by varunendra on 2014-03-07
I think it is safe to delete or move that file to let the system create a new one.

I have never tested it myself, to either wait for input from others, or try it at your own risk -
```
mv .ICEauthority Old.ICEauthority
```
..assuming you can log in and open the terminal or tty1 (Ctrl-Alt-F1) to run above. Else you can do the same from a live DVD/USB.

Log out --> Re-Login or reboot and see if the error is gone.

Once again - I'd wait for input from others. I have seen people doing this and be able to log in successfully, but am not sure if it is always safe.

---

### Post by jrmchess on 2014-03-07
> **varunendra said:**
> I think it is safe to delete or move that file to let the system create a new one.

I have never tested it myself, to either wait for input from others, or try it at your own risk -
```
mv .ICEauthority Old.ICEauthority
```
..assuming you can log in and open the terminal or tty1 (Ctrl-Alt-F1) to run above. Else you can do the same from a live DVD/USB.

Log out --> Re-Login or reboot and see if the error is gone.

Once again - I'd wait for input from others. I have seen people doing this and be able to log in successfully, but am not sure if it is always safe.

I did ctrl-alt-f1 at the login prompt and when I did ls -d there is no output... :(

---

### Post by Bashing-om on 2014-03-07
jrmchess; Hi !

That ain't good ! Le't poke a bit deeper, 
Log onto the system as that "newuser" and post back the outputs of terminal commands:
```

ls -la .ICEauthority
ls -la .Xauthority

```

Gives an idea of how deep we got to go !

[INDENT]look'n before the 
[INDENT][INDENT][INDENT]leap
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jrmchess on 2014-03-07
> **Bashing-om said:**
> jrmchess; Hi !

That ain't good ! Le't poke a bit deeper, 
Log onto the system as that "newuser" and post back the outputs of terminal commands:
```

ls -la .ICEauthority
ls -la .Xauthority

```

Gives an idea of how deep we got to go ![INDENT]look'n before the[INDENT][INDENT][INDENT]leap
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I am not able to login as the new user. the kde prompt comes up with the old user name. when I delete the old name and try to login it doesn't let me



Sorry I did cd home/<new user>/ and then ls -a but could only find the following <quote> . .. .bash_logout .bashrc examples.desktop .profile</quote>

---

### Post by Bashing-om on 2014-03-07
jrmchess; Umphhh .

Maybe getting in too deep for my pay grade.

OK, let's try this approach:
Boot the install to the GUI log in, and rather than logging into the system here, let's try from a console.

At the GUI log in do: -> key combo ctl+alt+F1 to get to a console.

Can you now log onto the system with the "NewUser" name and then enter the 
password as requested for that "newUser"( no response to the screen).

Now if you are able to login, do:
```

ls -la .ICEauthority
ls -la .Xauthority

```

maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT]

---

### Post by jrmchess on 2014-03-07
> **Bashing-om said:**
> jrmchess; Umphhh .

Maybe getting in too deep for my pay grade.

OK, let's try this approach:
Boot the install to the GUI log in, and rather than logging into the system here, let's try from a console.

At the GUI log in do: -> key combo ctl+alt+F1 to get to a console.

Can you now log onto the system with the "NewUser" name and then enter the 
password as requested for that "newUser"( no response to the screen).

Now if you are able to login, do:
```

ls -la .ICEauthority
ls -la .Xauthority

```

maybe yes[INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]


I had tried this before and tried it again now but it says login incorrect when I try to login with the new user name

---

### Post by jrmchess on 2014-03-07
> **jrmchess said:**
> I had tried this before and tried it again now but it says login incorrect when I try to login with the new user name

I also tried the following > chown <old name>:<old name> /[home[IMG]http://cdncache1-a.akamaihd.net/items/it/img/arrow-10x10.png[/IMG]]("http://forums.linuxmint.com/viewtopic.php?f=90&t=115076#")/old name/.ICEauthority 
chmod 0600 /[home[IMG]http://cdncache1-a.akamaihd.net/items/it/img/arrow-10x10.png[/IMG]]("http://forums.linuxmint.com/viewtopic.php?f=90&t=115076#")/old name/.ICEauthority with instructions from this site: [http://forums.linuxmint.com/viewtopic.php?f=90&t=115076](http://forums.linuxmint.com/viewtopic.php?f=90&t=115076) but still got the same error. I then tried to rename the file by using > mv /home/old name/.ICEauthority /home/old name/Old.ICEauthority but again the same error

one more thing I would like to add after I do a ctrl-alt-f1 and do an "ls" I get "examples.desktop"

---

### Post by Bashing-om on 2014-03-07
jrmchess; Well ! OK,

Got another thought.

Let me re-boot to grub's recovery console and check a thought.

I will be back in some bit.

[INDENT]which way did he go
[INDENT][INDENT]George
[/INDENT][/INDENT][/INDENT]

---

### Post by jrmchess on 2014-03-07
> **Bashing-om said:**
> jrmchess; Well ! OK,

Got another thought.

Let me re-boot to grub's recovery console and check a thought.

I will be back in some bit.
[INDENT]which way did he go[INDENT][INDENT]George
[/INDENT]
[/INDENT]
[/INDENT]


hey pls don't give up on me. I hope u will come back and solve my problem. This is my friend's computer and he is going to really flip if he knows what a stupid thing I did

---

### Post by Bashing-om on 2014-03-07
jrmchess; Welp:

That did not pan out, - looking at things from root access - I still see no way to access that /home directory.

Is there by some chance a "guest" account activated on the system ? If so maybe we can work something out from that account,

sometimes I just
[INDENT][INDENT]do not know
[/INDENT][/INDENT]

---

### Post by jrmchess on 2014-03-08
> **Bashing-om said:**
> jrmchess; Welp:

That did not pan out, - looking at things from root access - I still see no way to access that /home directory.

Is there by some chance a "guest" account activated on the system ? If so maybe we can work something out from that account,

sometimes I just[INDENT][INDENT]do not know
[/INDENT]
[/INDENT]


I can access the home directory from the command prompt now. I went ctrl-alt-f1. and cd /home/new user. I did an ls -a and got the following output:
> . .. .bash_logout .bashrc examples.desktop Old.ICEauthority .profile

The Old.ICEauthority file was copied by me from my old username folder and then renamed it

---

### Post by jrmchess on 2014-03-08
HAHAHA I SOLVED MY OWN PROBLEM ALL BY MYSELF:

This is what I did:

Followed instructions: > at the login screen 
             
[LIST=1]
[*]CTRL-ALT-F1 to get to terminal window
[*]sudo chmod 777 /home/xxx -R
[*]Switch back to the [login[IMG]http://cdncache1-a.akamaihd.net/items/it/img/arrow-10x10.png[/IMG]]("http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message#") screen by pressing Ctrl+Alt+F7 or F8
[/LIST]
      
 website reference: [http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message](http://askubuntu.com/questions/356284/cannot-login-after-update-ubuntu-12-04-iceauthority-error-message)

logged into kde and opened "KUser". I found that I had accidentally changed the path of the home directory. so changed it back to the old directory and now everything is running perfectly fine. I think I deserve a Nobel prize :)

---

### Post by varunendra on 2014-03-08
Congratulations!

But I choose to deny you the Nobel Prize because of the following "Oops!" step :p -
> sudo **[COLOR="#FF0000"]chmod 777[/COLOR]** /home/xxx -R
The "chmod 777 -R" command would have made all your files in your home directory 'readable, writable and executable' by "Everyone". Even if you are comfortable with the "Everyone" part, the 'executable' part can be (on 12.04, and after some changes on later ones - it WILL be) annoying. Because all the files will now be recognized as executable programs. ;)

The recommended way is to simply take the ownership of the files/directories recursively -
```
sudo chown -R user:user /home/*<the desired home directory>*
```
..where "**user**" is to be replaced by the new user id which you have created/changed.
This only changes the user and group of the files/directories, and keeps the other permissions same as they should be.

So I highly recommend to [FONT=Comic Sans MS][COLOR="#696969"]do a fresh install > deliberately mess up again > try the above fix instead (Just kidding ;p)[/COLOR][/FONT]

---

### Post by jrmchess on 2014-03-08
> **varunendra said:**
> Congratulations!

But I choose to deny you the Nobel Prize because of the following "Oops!" step :p -

The "chmod 777 -R" command would have made all your files in your home directory 'readable, writable and executable' by "Everyone". Even if you are comfortable with the "Everyone" part, the 'executable' part can be (on 12.04, and after some changes on later ones - it WILL be) annoying. Because all the files will now be recognized as executable programs. ;)

The recommended way is to simply take the ownership of the files/directories recursively -
```
sudo chown -R user:user /home/*<the desired home directory>*
```
..where "**user**" is to be replaced by the new user id who you have created/changed.
This only changes the user and group of the files/directories, and keeps the other permissions same as they should be.

So I highly recommend to [FONT=Comic Sans MS][COLOR=#696969]do a fresh install > deliberately mess up again > try the above fix instead (Just kidding ;p)[/COLOR][/FONT]

Thanks Varun,

so should the following step:

```
sudo chown -R user:user /home/*<the desired home directory>*
``` change the permissions back to their original settings?

I tried it and got the following error:

> chown: cannot access `/home/old user/.gvfs': Permission denied

---

### Post by varunendra on 2014-03-08
> so should the following step:
```
sudo chown -R user:user /home/*<the desired home directory>*
```
change the permissions back to their original settings?
Nope, it can't. It just changes the ownership, doesn't touch the read/write/execute permissions.

Not sure what the error was about or why it occurred, but even with no error, that command is not going to change anything except the ownership. If you need to revert the read/write/execute permissions to their original state, that would be a very cumbersome process now as you'll have to compare and change permissions of files/directories individually (or in very small groups) now, while comparing each with those on a standard installation.

Probably not worth trying unless you are having problems now and do need to keep this installation (yup, a fresh installation would be much quicker and simpler solution).

However, if you ARE having any problems now and do need to revert those permissions, let us know and we may try to help. But be aware it may be very time-taking process due to manually running similar commands (chmod <some permissions>) hundreds of times over individual files or small groups in your home directory.

If there is a way to automate this, I don't know of it yet.

---

### Post by jrmchess on 2014-03-08
> **varunendra said:**
> Nope, it can't. It just changes the ownership, doesn't touch the read/write/execute permissions.

Not sure what the error was about or why it occurred, but even with no error, that command is not going to change anything except the ownership. If you need to revert the read/write/execute permissions to their original state, that would be a very cumbersome process now as you'll have to compare and change permissions of files/directories individually (or in very small groups) now, while comparing each with those on a standard installation.

Probably not worth trying unless you are having problems now and do need to keep this installation (yup, a fresh installation would be much quicker and simpler solution).

However, if you ARE having any problems now and do need to revert those permissions, let us know and we may try to help. But be aware it may be very time-taking process due to manually running similar commands (chmod <some permissions>) hundreds of times over individual files or small groups in your home directory.

If there is a way to automate this, I don't know of it yet.

thanks for your help. no I don't want to revert back to the previous settings but I don't want any further problems coming up. U were saying that there could be some problems I may face because of my earlier solution which may cause all my files to be read as executable (something like that).  so will your suggestion help resolve this issue? how do I check if it has been resolved? Thanks

---

### Post by varunendra on 2014-03-08
Nope, it won't resolve it NOW. It was that should have been done instead of running chmod 777. Now that you have already done that, the command I suggested is useless for you.

And the problem is not related to the regular functionality of the OS. It is -

**1)** Risk that 'Everyone' will have full access to all the files/directories on your home. If it is a single user system or you are not too much concerned about security, that is not a problem.

**2)** All the files will be executable. This is frustrating when you double-click a file to open it, but instead of opening your file with a relevant program, the OS will present you with a dialogue box to ask whether you want to open it, or 'Run' it etc.

Besides these two, I can't think of any other serious problem. Also, the second problem may not be effective on most file types that are exclusively recognized as data files (like images, mp3s etc.). It will only be apparent when double-clicking file-types that are of dubious nature - mostly plain text files - that can be both data files or programs/scripts. And even that behaviour (with plain text files) is muted by default in 13.04 and later.

So unless you are already seeing some kind of annoying or confusing behaviour by your files, you don't really need to worry too much about that. :)

---

### Post by jrmchess on 2014-03-08
> **varunendra said:**
> Nope, it won't resolve it NOW. It was that should have been done instead of running chmod 777. Now that you have already done that, the command I suggested is useless for you.

And the problem is not related to the regular functionality of the OS. It is -

**1)** Risk that 'Everyone' will have full access to all the files/directories on your home. If it is a single user system or you are not too much concerned about security, that is not a problem.

**2)** All the files will be executable. This is frustrating when you double-click a file to open it, but instead of opening your file with a relevant program, the OS will present you with a dialogue box to ask whether you want to open it, or 'Run' it etc.

Besides these two, I can't think of any other serious problem. Also, the second problem may not be effective on most file types that are exclusively recognized as data files (like images, mp3s etc.). It will only be apparent when double-clicking file-types that are of dubious nature - mostly plain text files - that can be both data files or programs/scripts. And even that behaviour (with plain text files) is muted by default in 13.04 and later.

So unless you are already seeing some kind of annoying or confusing behaviour by your files, you don't really need to worry too much about that. :)

I have not faced problem #2 as of yet and as far as problem #1 goes this is my personal laptop. So do I need to worry about anything?

---

### Post by varunendra on 2014-03-08
I don't think you do.

It is not in the 'Standard' or recommended form, but it'll work.

---

