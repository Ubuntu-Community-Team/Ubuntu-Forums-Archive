---
title: "UT2004 Problems"
date: 2006-08-05
forum: Gaming &amp; Leisure
---

### Post by Steve4774 on 2006-08-05
Hello, everybody. Today I tried to install Unreal Tournament 2004 on Ubuntu, and I did it with linux-installer.sh. I restarted my computer when it had finished, and when I tried to run it I got this error:

steve4774@steve4774-desktop:~/Desktop/UT2K4$ sudo sh ut2004
ReadFile beyond EOF 0+4/0

History:

Exiting due to error

Can anybody help me with this?

---

### Post by FindWaldo on 2006-08-05
Try draging the linux-installer.sh into your home folder and running it from there.

---

### Post by Steve4774 on 2006-08-05
No, I installed it successfully. Sorry that was a little vague.

When I try to run the game it gave me that error.

---

### Post by Perfect Storm on 2006-08-06
You should not run ut2004 with root priviledge (it's bad karma ;) ), and you don't need to reboot on a linux system (only in rare cases like kernel and the like).

Check [http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

You'll need to uninstall ut2004 first and remove /.ut2004 in your home folder first (it's hidden).

---

### Post by Steve4774 on 2006-08-06
"You are not authorized to view this resource." is what I get when I try to look at that link, and I made an account.

I got rid of the /.ut2004 folder and everything that was in it, but when I try to run ut2004 again, it makes a folder by the name of .ut2004 in the same place. Should I not try to run it again and get rid of that.

Also, what would uninstalling ut2004 do? I'm not sure I understand what you mean. 

Anyways, when I try running the uninstaller, it says it can't find a usable uninstall program. Could anybody direct me towards one?

---

### Post by _simon_ on 2006-08-06
Hi,

The problem is that you are trying to run it with the wrong command.

You simply need to specifiy the location of ut2004

For example.

If you installed it to /home/steve/ut2004

From terminal you would enter:

/home/steve/ut2004/ut2004

If you installed it anywhere other than /home you may need to fiddle with privledges.

---

### Post by Steve4774 on 2006-08-06
I have it installed at /usr/local/games/ut2004, and I tried typing ut2004 in that directory, and then: sudo sh ut2004   None of them worked.

```
steve4774@steve4774-desktop:/usr/local/games/ut2004$ ut2004
ReadFile beyond EOF 0+4/0

History:

Exiting due to error
steve4774@steve4774-desktop:/usr/local/games/ut2004$ sh ut2004
ReadFile beyond EOF 0+4/0

History:

Exiting due to error
steve4774@steve4774-desktop:/usr/local/games/ut2004$

```

That was the process of it.

How would I change the privileges to make this game work?

---

### Post by _simon_ on 2006-08-06
Try this from terminal:

```

sudo chown -R steve4774:steve4774 /usr/local/games/ut2004

```

Enter your password when prompted.

Then try and run it, so again from terminal enter ONLY this:

```

/usr/local/games/ut2004/ut2004

```

---

### Post by Steve4774 on 2006-08-06
No luck on that, _simon_.

---

### Post by _simon_ on 2006-08-06
I'd try installing to to /home then and see what happens. That way you know 100% that you have the correct privladges.

If you still get any kind of error then let us know what it is.

---

### Post by Steve4774 on 2006-08-06
Alright, I guess I made some "progress".

```
steve4774@steve4774-desktop:/home$ sudo sh ut2004
Assertion failed: InPos<=Size [File:../../Core/Inc/FFileManagerLinux.h] [Line: 82]

History:

Exiting due to error

```

Any ideas?

---

### Post by _simon_ on 2006-08-06
lol stop using sudo sh!

sudo is used for super user privledges.

If you have now installed to /home you don't need sudo.

You don't need sh to run a program.

The file that executes for ut2004 is ut2004.sh

So to launch ut2004 you need to execute ut2004.sh

I honestly haven't got a clue what that latest error you have is but try launching the game properly and see what happens.

I don't know where you have installed it to now but the commant you enter in terminal would look something like this:

/home/steve4774/ut2004/ut2004

You don't need any sudo or sh in front of that.

Oh and one other thing... if you installed to /home using sudo then you'll still have the same problem.

install using just sh nameofinstaller.sh

---

### Post by Steve4774 on 2006-08-06
Well, I got it to work. All I had to do was get something called a UT2004 megapack. I installed that, ran ut2004, and it works perfectly.

---

