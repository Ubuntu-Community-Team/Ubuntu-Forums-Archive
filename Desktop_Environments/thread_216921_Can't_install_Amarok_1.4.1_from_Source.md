---
title: "Can't install Amarok 1.4.1 from Source"
date: 2006-07-16
forum: Desktop Environments
---

### Post by citizenkeith on 2006-07-16
I've managed to run .configre, but when I run make I get this error:

```
make[3]: Entering directory `/home/keith/Desktop/amarok-1.4.1/doc/ru'
make[3]: *** No rule to make target `config_scrobbler.png', needed by `index.cache.bz2'.  Stop.
make[3]: Leaving directory `/home/keith/Desktop/amarok-1.4.1/doc/ru'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keith/Desktop/amarok-1.4.1/doc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keith/Desktop/amarok-1.4.1'
make: *** [all] Error 2

```

Not sure how to proceed from here...  ](*,)

---

### Post by GarethMB on 2006-07-16
Why compile from source?

You can get it through apt-get.

[http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

---

### Post by citizenkeith on 2006-07-16
> **GarethMB said:**
> Why compile from source?

You can get it through apt-get.

[http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

When I get to the final step:

```
deb http://kubuntu.org/packages/amarok-141 dapper main
```

I get "bash: deb: command not found."

Obviously, there's a different command that I need to use, I just don't know what it is.

---

### Post by christhemonkey on 2006-07-16
You need to add that line to the end of your sources.list file.

```
gksudo gedit /etc/apt/sources.list 
```
And then add the line:
> deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main
To the end.
Then save and quit.

---

### Post by asimon on 2006-07-16
> **citizenkeith said:**
> When I get to the final step:

```
deb http://kubuntu.org/packages/amarok-141 dapper main
```

I get "bash: deb: command not found."

Obviously, there's a different command that I need to use, I just don't know what it is.
You should not enter this line in the command line but add this line to the file '/etc/apt/sources.list'. If you have done this, update your package list with the command 'sudo apt-get update', then you can install the new amarok with the command 'sudo apt-get install amarok'. The instructions on kubuntu.org could be a little bit more clear on this, of course not everyone knows what to do with an 'Apt source' line.

You can also also do all of these steps with a graphical tool like adept or synaptic, but this should better be explained by someone who actually uses them. ;-)

---

### Post by GarethMB on 2006-07-16
Start Adept.

Click Adept > Manage Repositories

Copy:

```
deb http://kubuntu.org/packages/amarok-141 dapper main
```

And Paste:

Into the form at the bottom of the window "New Repository"

Click Add

Click Apply

Click "Fetch Updates" to reload the repositories.

Amarok 1.4.1 Can now be installed.

---

### Post by citizenkeith on 2006-07-16
Thanks everybody. I can't believe I forgot that... new user here, so thanks for your patient answers. :)

I managed to update, but now Amarok won't play FLAC files. I've been told to update to xine-lib 1.1.2, but that didn't help. :(

---

### Post by GarethMB on 2006-07-17
Sorry, but i think you'll have to wait until xine is updated, as Amarok has to be rebuilt when xine is changed...which would leave you with the same build problem. 

I tried building Xine, but i'm not sure how good it was, and as I have no FLAC files at the minute, i didn't feel like rebuilding Amarok from source.

---

### Post by GarethMB on 2006-07-17
I have the fix. It was posted on these forums. Here is the link to the thread.

[http://ubuntuforums.org/showthread.php?t=210683&page=2&highlight=xine+1.1.2](http://ubuntuforums.org/showthread.php?t=210683&page=2&highlight=xine+1.1.2)

---

### Post by citizenkeith on 2006-07-17
> **GarethMB said:**
> I have the fix. It was posted on these forums. Here is the link to the thread.

[http://ubuntuforums.org/showthread.php?t=210683&page=2&highlight=xine+1.1.2](http://ubuntuforums.org/showthread.php?t=210683&page=2&highlight=xine+1.1.2)

Thanks! I'll try it tonight when I get home from work (ssh... I shouldn't be posting right now :D ).

I had built xine-lib from source, but it still wasn't working. A developer on the Amarok forums suggested that, even though I built xine-lib 1.1.2, Amarok was probably still using the old version.

---

### Post by citizenkeith on 2006-07-17
GarethMB,

Thank you so much, It fixed BOTH Amarok/Flac problems that I was experiencing. :)

---

