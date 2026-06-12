---
title: "need help with installing and configuring wine"
date: 2006-08-02
forum: Desktop Environments
---

### Post by fouadk on 2006-08-02
help im new in linux...
i need detailed help in installing and configuring wine
i also need help in installing games and how to make them work...
i tryed to install a game called USAF that is made of two CD's when the game ask for the second CD ,i insert it and press the OK button in order to continue ,it doesnt it keeps asking for it...
is there any complete guide for wine on the net???
please help

---

### Post by cantormath on 2006-08-02
> **fouadk said:**
> help im new in linux...
i need detailed help in installing and configuring wine
i also need help in installing games and how to make them work...
i tryed to install a game called USAF that is made of two CD's when the game ask for the second CD ,i insert it and press the OK button in order to continue ,it doesnt it keeps asking for it...
is there any complete guide for wine on the net???
please help

What are trying to install with wine?

If you are looking to install word, photoshop etc..........use [crossover]("http://www.codeweavers.com/products/cxoffice/").  It will set your wine up and work well.  It also makes it easy to install programs written from windows.

If you are just trying to install games make for windows, ie) halo, counterstrike etc, use [cedega]("http://www.transgaming.com/").

---

### Post by fouadk on 2006-08-02
man i know cedega but its not free like wine...
i wanna wine for gaming purposes...

---

### Post by cantormath on 2006-08-02
> **fouadk said:**
> man i know cedega but its not free like wine...
i wanna wine for gaming purposes...

Regarding cedega, there are some [options]("http://torrentspy.com/torrent/537885/Cedega_5_1_all_file_types")
or [options]("http://torrentspy.com/search.asp?h=&query=cedega&submit.x=0&submit.y=0") depending on what country you may live in, or your ethics.

The easiest way to install wine is with Automatix.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)


If you want to do it more manually.....
I think wine is in the normal repos. If not, uncomment the Universe repos in your /etc/apt/source.list

1 Install wine
Code:

sudo apt-get update
sudo apt-get install wine


2 Setup disc drives in wine
Code:

winecfg

Go to the Drives tab.
Press the Autodetect button.
Press the Show Advanced button.
Change the type of your CD drive(s) to CD-ROM.

3 Test audio in wine
Code:

winecfg

Go to the Audio tab.
If it crashes follow the instructions here.
[http://www.ubuntuforums.org/showpost...65&postcount=7](http://www.ubuntuforums.org/showpost...65&postcount=7)


NOTE
here are the bleeding edge repos for wine.

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

NOTE 
this is an interesting thread about setting up cvscedega, but i have not tried it.
[http://ubuntuforums.org/showthread.php?t=193814&highlight=wine+gaming](http://ubuntuforums.org/showthread.php?t=193814&highlight=wine+gaming)

---

### Post by Mimsy on 2006-09-30
> **cantormath said:**
> 3 Test audio in wine
Code:

winecfg

Go to the Audio tab.
If it crashes follow the instructions here.
[http://www.ubuntuforums.org/showpost...65&postcount=7](http://www.ubuntuforums.org/showpost...65&postcount=7)


Sorry to dig up such an old thread, but I have that very problem. I recently installed wine, updated it and all that, and opened winecfg to configure it. Wine crashes when I come to the Audio tab, and the link above leads to the forum start page. I tried to search the forums for the thread, but came up with a few hundred threads or none at all, depending on my search terms.

Where are these isntructions? I'd enjoy sound in wine. :)

Thanks,
Mimsy

---

