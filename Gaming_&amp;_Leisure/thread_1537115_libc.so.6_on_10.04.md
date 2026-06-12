---
title: "libc.so.6 on 10.04?"
date: 2010-07-23
forum: Gaming &amp; Leisure
---

### Post by karimruan on 2010-07-23
I have just recently installed Path of Magic on my ubuntu netbook remix 10.04, but it will not run. I got to once, with some tweaking, but could not do it again (I don't remember what I did!)

When I run the pathofmagic_start script I get the following error:

```

./Path_of_Magic: /usr/local/PathofMagic/libc.so.6: version `GLIBC_2.11' not found (required by /usr/lib/libGLU.so.1)

```

When I try to run the executable I get a 
```

Failed to change to directory '"/usr/local/PathofMagic"' (No such file or directory)

```

I did this install as sudo (probably dumb, but I just want it to work) and it defaulted to /usr/llocal/

Previous installs put it in my home directory. Same results though, jsut different paths.

The pathofmagic_start script looks like this:

```

export LD_LIBRARY_PATH="/usr/local/PathofMagic":.
cd "/usr/local/PathofMagic"
./Path_of_Magic

```

I tried first deleting the first line, since I should have libc,so.6 (apt says it is there), still not working.

Tried deleting the second line to fix the failure to change directory (the script is in the install directory) and still didn't work.


Any Idea?

---

### Post by regala on 2010-07-23
> **karimruan said:**
> 
```

./Path_of_Magic: /usr/local/PathofMagic/libc.so.6: version `GLIBC_2.11' not found (required by /usr/lib/libGLU.so.1)

```

Any Idea?

delete the file libc.so.6 located in /usr/local/PathofMagic/ and it might work -- at least it would try not to use another libc than the one shipped by your distributor (game bundlers...)

---

### Post by karimruan on 2010-07-23
> **regala said:**
> delete the file libc.so.6 located in /usr/local/PathofMagic/ and it might work -- at least it would try not to use another libc than the one shipped by your distributor (game bundlers...)

Thanks for the idea, unfortunately, it just returns another error:

```


appstub.linux signal handler 11karim@Komputileto:~/PathofMagic$


```

I am used to getting errors about missing dependencies, but this one is new.

I will try to provide as mucb relevent info on the setup as possible.

Game is installed in my home directory. I have executables there, which give me the failed to change directory message when double clicked. The executable 'Path of Magic' which has a custom icon has the following command for execution in properties:

```

"/home/karim/PathofMagic/pathofmagic_start"

```
so clicking this icon is basically just running the script from my first post. This icon gives me the:

```

Details: Failed to change to directory '"/home/karim/PathofMagic"' (No such file or directory)

```

The readme says I might have to run the script in terminal, so I fired it up, and did ./pathofmagic_start to get the original 'libc.so.6' error. After removing libc.so.6 I get the new error above.

I got it to work once, by editing the properties of the icons, the pathofmagic_start script, and running through terminal. But, I cannot remember exactly what it was I did that worked, as I did alot of tinkering with high hopes.

---

### Post by karimruan on 2010-07-23
After some extensive google pillaging, I finally have a clearer picture. The game was probably compiled with an older compiler, as it was built on ubuntu 7.04.

still not sure why I got it to work that once, even though I cannot remember how.

Anyway, is there any way of setting up a virtual compiler that would run the game? If I could have the needed compiler in the games install directory, without having to recompile ubuntu, or affect my current compiler, that would be ideal. I am for now trying to avoid running 7.04 in vbox simply because I bought the game for my wife, who is not going to want to boot into lucid, run vbox, just to boot into 7.04 to lay the game. lol.

So, i assume it all comes down to the versions of my c compiler. I guess the version that ships with lucid is not backwards compatible with the compiler the game requires?

Any easy ish workarounds, without affecting the ability to play more modern games (this system is our dedicated gaming machine, and we will not put windows on it, haven't use that crap for the last 1 1/2 years, no need to go back now)


Thanks again


NOTE: When I got it to run, I did alot. I edited the pathofmagic_start script, changed the command of the Path of Magic executable in it's properties, created my own script in my home folder (path of magic is installed to home/user/PathofMagic/)

Not exactly sure what changes I made, but I have been unable to replcate them at all. Oh, I also had an error first about libc.so.5 or something, installed it with a DEB. Played it for about 10 minutes, liked it.I exited and then tried to rerun to see if it would still work, but could not remember how I ran it. I know it was through terminal.

Path of Magic is the same as Runes of Avalon, in case it matters. Same game, just a sequel I guess.

---

### Post by karimruan on 2010-07-24
bump... :)

Please, somebody has to have an idea... I have been messing with the script and other contents of the PoM folder for a couple of days now, trying to replicate the changes I made. 

I know there are crap loads of linux gods on this forum... please, will one of them throw me a scroll or something! lol

I will provide any info you need, even the installer if you want, I just want to have my wife enjoying my $9, instead of chucking it as a loss because the company is just a ad about communicated as tuxgames :(

All I know is it was built on 70.04 and I am on 10.04, so obviously the libraries have been upgraded. Is there a way around this without recompiling ubuntu? 

By the way, Runes of Avalon 2 demo works fine, i have even tried copying all the properties of each executable, editing them with PoM's info, and all. No luck :(

---

### Post by karimruan on 2010-07-24
Okay, I figured it out! All I did was change the pathofmagic_startup script from the install directory, and added in sudo, so the last line changed from ./Path_of_Magic to sudo ./Path_of_Magic. 

Works fine now. All that stuff I tried, and te simplest of things I didn't even think about ended up solving the problem.

Now, is there a way to run without sudo??? Oh well, that is another thread, another day possibly. 

Mods: If this is not marked as solved, could you please mark it solved for me? :)

---

