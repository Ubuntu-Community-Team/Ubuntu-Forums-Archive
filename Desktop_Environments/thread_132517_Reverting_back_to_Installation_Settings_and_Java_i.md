---
title: "Reverting back to Installation Settings and Java installing"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Enforcer on 2006-02-18
Ok i was able to redo my uncles pc last night again, it all works except Java, ive seen several posts on installing java and i tried Autmatix, didnt work. Says it installed it ok but java doesnt load on the sites at all. (Whats the Terminal cmd to check the java version again, <<Newbie to linux, luv it tho very nice os)

I have about 6 hrs to get java working on here, cause its gotta go back to my uncles house. And currently this is the only thing stopping me frm bringing it back earlier!!!<<<<<< :-)

Any help. ill search the forums again but if you've gotten it to work yourself please let me know!

---

### Post by nalmeth on 2006-02-18
can you post what went wrong with the automatix installation of java? Did you install jre1.5 or the sdk 1.5?

---

### Post by Enforcer on 2006-02-18
-=Edited by Enforcer=-

---

### Post by Enforcer on 2006-02-18
-=Edited by Enforcer=-

---

### Post by Enforcer on 2006-02-19
k i was able to install flash ok and that works but still cant get java to work even tho i installed it

i used this wiki page here : [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) 

and the flash worked but java didnt

i followed the tut changing the paths from this

```
sudo bash

chmod 777 ./jre-1_5_0_06-linux-i586.bin

(this file name will depend on the java version you download)

./jre-1_5_0_06-linux-i586.bin

(it will ask you some questions)

mkdir /usr/local/java32

cp -r -p ./jre1.5.0_06/* /usr/local/java32

cd /usr/local/firefox32/plugins/

ln -s /usr/local/java32/plugin/i386/ns7/libjavaplugin_oji.so ./ 
```

to this

```
sudo bash

chmod 777 ~/Desktop/jre-1_5_0_06-linux-i586.bin

(this file name will depend on the java version you download)

~/Desktop/jre-1_5_0_06-linux-i586.bin

(it will ask you some questions)

mkdir /usr/lib/java

cp -r -p ./jre1.5.0_06/* /usr/lib/java

cd /usr/lib/mozilla-firefox/plugins/

ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./ 
```

now the last line cmd there the 'ln -s blah blah blah' says the file already exists. This should work ok tho, unless i , hmm let me test something right quick

Edited:
K what i jsut tried was cd-ing to the usr/lib/mozilla/ and using this ln -s /usr/lib/java/plugin/i386/ns7/libjavaplugin_oji.so ./  to create or copy (not sure what this does if anyone wants to clerify) and i guess that worked but Java still inst working. So if anyone could help that b great!

---

