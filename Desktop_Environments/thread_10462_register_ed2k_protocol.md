---
title: "register ed2k protocol?"
date: 2005-01-08
forum: Desktop Environments
---

### Post by GeneticFreek on 2005-01-08
Hi there

I've installed aMule after getting frustrated with mldonkey. How do I register aMule to handle ed2k links? Currently I have to "copy link location" then paste it into aMule.

GeneticFreek

---

### Post by ow50 on 2005-01-08
Install [mozex](http://mozex.mozdev.org/) and if you're using firefox install [show old extensions](http://www.pikey.me.uk/mozilla/#soe) as well.

At terminal type "locate ed2k"
In the mozex settings under "ED2K" put "/usr/local/bin/ed2k %r" or whatever you got with locate.

This is quite complicated, but i don't know of an easier way.

Also check the [amule wiki](http://www.amule.org/wiki/index.php/Ed2k_links_handling) although it's partly outdated.

---

### Post by GeneticFreek on 2005-01-08
[QUOTE=ow50]Install [mozex](http://mozex.mozdev.org/) and if you're using firefox install [show old extensions](http://www.pikey.me.uk/mozilla/#soe) as well.

At terminal type "locate ed2k"
In the mozex settings under "ED2K" put "/usr/local/bin/ed2k %r" or whatever you got with locate.

This is quite complicated, but i don't know of an easier way.

Also check the [amule wiki](http://www.amule.org/wiki/index.php/Ed2k_links_handling) although it's partly outdated.[/QUOTE]
 The command "locate ed2k" comes up with nothing for me. And "locate amule" just find the .deb file. Help!

GeneticFreek

PS...I am still new to linux and this is one thing that frustrates me....I don't know where anything is (supposed to be) stored, and I don't know how to find it either!

---

### Post by ow50 on 2005-01-08
[QUOTE=GeneticFreek]The command "locate ed2k" comes up with nothing for me. And "locate amule" just find the .deb file. Help![/QUOTE]
```
sudo locate -u
```
This will refresh your database for locate (might take a couple minutes). You might have noticed that locate is very fast, that's because it doesn't go through your files, just a database of them. Your ed2k executable should be either at /usr/bin or /usr/local/bin so you can experiment if you want to skip the locating.
----------------
I wrote in my earlier post that amule wiki would be outdated but the directions at [[link](http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later))] might be enough. I personally like mozex because it makes it easier to setup all different protocols.

---

### Post by GeneticFreek on 2005-01-08
[QUOTE=ow50]```
sudo locate -u
```
This will refresh your database for locate (might take a couple minutes). You might have noticed that locate is very fast, that's because it doesn't go through your files, just a database of them. Your ed2k executable should be either at /usr/bin or /usr/local/bin so you can experiment if you want to skip the locating.
----------------
I wrote in my earlier post that amule wiki would be outdated but the directions at [[link](http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later))] might be enough. I personally like mozex because it makes it easier to setup all different protocols.[/QUOTE]
 Thank you! The locate -u worked and now I can click on ed2k links!

Cheers

---

### Post by Poul on 2005-05-07
There is easier (and more clean) solution:
[http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later)](http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later))

---

### Post by Sav on 2005-06-29
[QUOTE=Poul]There is easier (and more clean) solution:
[http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later)](http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later))[/QUOTE]

I follow the guide, but nothingh changed:

> Mozex doesn't work anymore with Mozilla 1.7 and Firefox 0.9. There is an alternate method that seems to be working with both of them:

    * Remove MozEx if installed or at least remove the ed2k input from it (only if MozEx is installed) 

    * Insert about:config in the address bar 

    * Right click on the list, select New, then Boolean; insert network.protocol-handler.external.ed2k as Preference Name and true as Value 

    * Now another right click, select New and String; insert network.protocol-handler.app.ed2k as Preference Name and /path/to/ed2k (path to where the file is installed on your system) as Value. 

The path for me is: usr/bin/ed2k

---

