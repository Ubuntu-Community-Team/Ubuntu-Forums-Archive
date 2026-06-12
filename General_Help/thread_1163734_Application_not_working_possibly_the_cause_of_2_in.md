---
title: "Application not working possibly the cause of 2 installs"
date: 2009-05-19
forum: General Help
---

### Post by ssanders4917 on 2009-05-19
I attempted to install songbird where i created a gedit script and then ran it in the terminal. When I tried to run the application I get the error: Failed to execute child process "Songbird" (No such file or directory)

I then installed again using a different method that resulted in the application working but when I closed it that is the last that I could use it. It does not show up in synaptic or add/remove. I cannot find a way to remove it at all to possibly try to reinstall it. any help would be great.

---

### Post by ssanders4917 on 2009-05-19
Anyone?

---

### Post by ssanders4917 on 2009-05-19
Well I guess I have either stumped everyone or I am just an idiot.

---

### Post by themusicalduck on 2009-05-19
What was in the script you first made and what was the 'alternative' method of installing it you tried?

---

### Post by ssanders4917 on 2009-05-19
Here is the first method that is not working.    [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

I then used this one and had success. I now see that I must create a menu shortcut for application but I would still like to remove the bad install. [http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

---

### Post by themusicalduck on 2009-05-19
If things are working then you probably don't have to worry too much about the other install. Someone else might know how to remove anything it left but if it didn't work then it probably won't have made many if any important changes to the system anyway.

I see on [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird) there are .debs available though, listed above the script part. Using .deb files are almost always the best way to install a program so if there's one available for a program I would use that from now on.

---

### Post by ssanders4917 on 2009-05-19
Thanks for looking. I just changed the command location of the non working to the one that worked.

---

### Post by SentientFluid on 2009-05-19
If *installsongbird.sh* can you run this in Terminal and copy and paste the result?

```
cd ~/Desktop
./installsongbird.sh
```

---

### Post by ssanders4917 on 2009-05-19
```
~/Desktop$ ./installsongbird.sh
bash: ./installsongbird.sh: No such file or directory
```

---

