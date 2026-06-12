---
title: "applet to run program as other user?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by wazoo on 2006-07-03
Breezy had an applet that let you run a program as another user. It was a nice, small, graphical way to login, type a password, then type a command. This was very handy for my assistant, so she could sync her Palm, then sync mine, and keep them both running.

But it's gone in Dapper! And one of the likely workarounds I found (sudo -u bob -i jpilot) just flat out didn't work.

Any ideas?

---

### Post by Jucato on 2006-07-03
It's still installed, but not enabled in the menus.
Launch Alacarte Menu Editor. Under Applications > System Tools, look for "Run as different user" and enabled/check it. It will be added to your menu.

---

### Post by wazoo on 2006-07-03
Thank you! However, it doesn't work. At least, it doesn't work for jpilot and my test account. Could you see if it works for you?

1. Adduser (I added "test" with the password of "test.")
2. Run the "run as different user" program, using "test" as the user and anything you've got on your system -- gedit, say.
3. Click OK.

I tried it with the "test" password (didn't work at all, and got an error message). Then I tried my superuser password, which did work -- except, nothing happened. No error message, no gedit.

[Scratches head.]

---

### Post by Jucato on 2006-07-03
<scratched head, too>
You're right, it does seem strange. Also, it doesn't specify which password you should enter: the 2nd user's password, or the admin's password. It seems that root is the only "other user" that's working with that.

Let's wait, maybe someone has an idea...

<still scratching head>

---

### Post by mannheim on 2006-07-03
You can get an idea of what is going on (I think, but not a solution) by using sudo at the terminal. Assuming your own username is joe, and your other user is "test", try an innoccuous terminal command like "ls /":

```
joe@somewhere:~$sudo -u test ls /
Password: <enter joe's password>
```

The above command should work, as long as joe is allowed to use sudo (i.e. as long as joe is in the admin group). Now try the same thing with gedit:

```
joe@somewhere:~$sudo -u test gedit
Password: <enter joe's password>
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

```

So it's a problem with authorities/permissions in X.

---

### Post by Jucato on 2006-07-03
yeah I get the same error messages. Is that normal? I mean, is that supposed to be how Linux/Ubuntu works? Or maybe there's a specific user setting that must be enabled?

---

### Post by wazoo on 2006-07-04
Right, I can run any NON-GRAPHIC program - anything that doesn't use X? But this used to work, people!

---

### Post by mannheim on 2006-07-04
[QUOTE=mannheim]You can get an idea of what is going on (I think, but not a solution) by using sudo at the terminal. Assuming your own username is joe, and your other user is "test", try an innoccuous terminal command like "ls /":

```
joe@somewhere:~$sudo -u test ls /
Password: <enter joe's password>
```

The above command should work, as long as joe is allowed to use sudo (i.e. as long as joe is in the admin group). Now try the same thing with gedit:

```
joe@somewhere:~$sudo -u test gedit
Password: <enter joe's password>
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

```

So it's a problem with authorities/permissions in X.[/QUOTE]

I've got it, I think. It is the read permissions on the .Xauthority file in joe's home directory. Try this:

```
[COLOR="Blue"]joe@somewhere:~$[/COLOR] chmod go+r ~/.Xauthority
```

Then try again:

```
[COLOR="Blue"]joe@somewhere:~$[/COLOR] sudo -u test gedit
Password: <enter joe's password>

```

This should work now. So should the gui launcher versions, I think.

---

### Post by mannheim on 2006-07-04
[QUOTE=mannheim]Try this:

```
[COLOR="Blue"]joe@somewhere:~$[/COLOR] chmod go+r ~/.Xauthority
```
[/QUOTE]

Someone should probably comment on whether this is a good idea as far as security goes: it probably isn't. I think that doing this allows anyone else who is logged in to the machine to access the same X server that joe is using. This must be bad in a truly multi-user environment where you don't necessarily trust every user who as an account on the machine.

---

### Post by wazoo on 2006-07-06
Well, good idea or not, I tried it, and here's the interesting thing. 

I did run the command, as my current user (which has administrative privileges)
chmod go+r ~/.Xauthority

Then, when I try to run jpilot in my test account (through "Run as different user" menu), still no good. But it WILL run as root.

The sudo su -u command works though. Thanks!

---

