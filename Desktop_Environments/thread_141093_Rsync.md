---
title: "Rsync"
date: 2006-03-07
forum: Desktop Environments
---

### Post by 1oki on 2006-03-07
Can someone tell me how to get Rsync to work... I know there are other things out there such as Unison that might be easier, but I need Rsync... I am trying to sync my samba share with another samba share on the network. This network samba share is on a Terastation and I belive uses rsync, hence the resaion why I need rsync and not another option! thanks! ;)

---

### Post by Xian on 2006-03-07
This explains it better than anything I could say: [Rsync How-To](http://www.ss64.com/bash/rsync.html).

---

### Post by 1oki on 2006-03-07
thanks!

---

### Post by 1oki on 2006-03-08
sweet, I got rsync working... now two other questions that I didnt find the answer to on that page. 

1. can I make this automated?
2. How can I exclude a directory? I am making a backup of the whole system and am sending that backup to a mounted directory. So instead of an infinit copy of the mount, I would like to exclude that directory... any thoughts? thanks

---

### Post by art on 2006-03-08
make a cron job do the rsync at certain times.

---

### Post by 1oki on 2006-03-08
oh yeah... Why didnt I think of that... thanks guys for all your help!

---

### Post by AirOnSkin on 2007-09-05
hey guys

i sync my data disk with a backup disk and an external disk. i've two questions. if anybody can help, i would be very happy.

1: i'm using the option -c (checksum check). it works fine and it does exactly what i want. with that option it only copies the changed files from the source to the destination. unfortunately it's extremely slow. is there a way to have the same effect (only copying the new/changed files) with an other (faster) option? with -u (update) it copied all files --> stupid

2: in the script to sync to my external dsik i want to exclude 4 directories. i defined them with the --filter option. actually only 3 of them are filtered and i have no idea why the 4th one (the first in the script) isn't listed.

this is the script:
```
#!/bin/bash
rsync -r -c -vv --progress --max-size=4G --delete --filter="- zgames/" --filter="- incoming/" --filter="- movies/" --filter="- music/" /media/data /media/charlie
```
it doesn't filter "zgames"

the folder paths are:
/media/data/06-windows/setups/zgames
/media/data/07-temp/downloads/incoming
/media/data/07-temp/downloads/movies
/media/data/07-temp/downloads/music

when i start the script it says:
```

building file list ... 
[sender] hiding directory data/07-temp/downloads/music because of pattern music/
[sender] hiding directory data/07-temp/downloads/incoming because of pattern incoming/
[sender] hiding directory data/07-temp/downloads/movies because of pattern movies/
 700 files...

```

any ideas :?:

air

---

### Post by wwuster on 2007-09-07
Is it possible to use rsync to just get a list of files that are different on two machines? I have 2 machines with the same directory name containing about 30000 files. I'd just like to see which files are different between the two machines.

thanks,
William

---

### Post by AirOnSkin on 2007-09-07
just build yourself a sync-job like you would sync the two folders but add --list-only to the syntax. then you get kind of a prview...

---

