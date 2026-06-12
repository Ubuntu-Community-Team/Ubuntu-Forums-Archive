---
title: "Punkbuster Installation Problem"
date: 2008-06-02
forum: Gaming &amp; Leisure
---

### Post by RobOrr on 2008-06-02
First off, sorry to anyone who read this in the Wine forum, I was very tired last night when I posted that. :D
Hey everyone, I've just started playing Wolfenstein: Enemy Territory online with Ubuntu, and everything works fine as long as I don't try to join a punkbuster enabled server, at which point it just awaits challenges indefinitely. I tried god knows how many ways to get pbsetup.run to install but it's refusing, returning
> pbsetup.run: command not found.

It's the correct binary file from the punkbuster website, and everyone else on this forum seems to have had no problems getting the file to install normally.Here's things I've tried:
> desktop:~/Punkbuster$ sudo bash pbsetup.run
pbsetup.run: pbsetup.run: cannot execute binary file
desktop:~/Punkbuster$ sudo chmod -c u+x pbsetup.run
desktop:~/Punkbuster$ pbsetup.run
bash: pbsetup.run: command not found


any help would be greatly appreciated:D

---

### Post by jolx on 2008-06-02
if you've made it executable all you need to do is double click on it in nautilus and choose to run in terminal

---

### Post by RobOrr on 2008-06-02
the problem is that double clicking it, or running it in the terminal, even though it's explicitly been set as an executable, produces absolutely no output, as if I never tried to execute it.

---

### Post by Cappy on 2008-06-02
```
chmod 755 ~/Punkbuster/pbsetup.run
```
to make sure the permissions are correct

and then use

```
~/Punkbuster/pbsetup.run
```
or
```

cd ~/Punkbuster
./pbsetup.run

```

---

### Post by RobOrr on 2008-06-03
> 
:~$ chmod 755 ~/Punkbuster/pbsetup.run
:~$ cd ~/Punkbuster
:~/Punkbuster$ ls
pbsetup.run
:~/Punkbuster$ ./pbsetup.run
:~/Punkbuster$ pbsetup.run
bash: pbsetup.run: command not found
:~/Punkbuster$ 


Still no luck I'm afraid. I also repeated these commands with sudo, and tried  them all with a new copy of the pbsetup.run file. It's a mystery to me why this is being so awkward.

---

### Post by nothingtoprove on 2008-06-03
Hi
Completely new user and first time poster so please be gentle.
I've been through all the threads I can find on this and seem to have a similar problem.

I'm stuck "Awaiting Challenge" since I installed TCE (this morning).

As far as I can work out I no longer have permissions in the pb folder.
I have tried the chmod suggestions here [http://ubuntuforums.org/archive/index.php/t-585938.html](http://ubuntuforums.org/archive/index.php/t-585938.html) when I run pbsetup I get a permission denied error (Directory '/usr/local/games/enemy-territory/pb/dll/' couldn't be created (error 13: Permission denied)

As I mentioned I'm literally a couple of days into Ubuntu having migrated from XP so I only have those two days experience.

Any help greatly appreciated!

---

### Post by RobOrr on 2008-06-03
If you're stuck on awaiting challenge it means that Punkbuster isn't running and therefore cannot receive the challenge from the Punkbuster program on  the server, that much I've found out :D

If your permissions are denied, try installing and 'chmod'ing with the sudo command as a prefix i.e.

> sudo pbsetup.run

> sudo chmod 755 pbsetup.run

if you check the properties of the file in nautilus (right-click and select properties) you can see the permissions of the file i.e. who owns it, what they're allowed to do with it, and what everyone else is allowed to do with it. If they're all set to read-only or if root is the only user that's allowed to use it, then that's where the problem is (I hope).

---

### Post by nothingtoprove on 2008-06-03
pbsetup is working okay - it just can't update the files in the pb folder in ET.
I have no permissions over these and I think that is where the problem is, as they can't be modified.

---

### Post by RobOrr on 2008-06-03
Note about my specific problem: It appears that I also cannot run pbsetup.exe, the windows installer through wine, in that nothing happens when I double click the file.

---

### Post by RobOrr on 2008-06-04
Problem solved. An update from Gutsy to Hardy fixed the problem and punkbuster installed perfectly.

---

