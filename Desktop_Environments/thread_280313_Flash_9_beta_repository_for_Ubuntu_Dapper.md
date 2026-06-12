---
title: "Flash 9 beta repository for Ubuntu Dapper"
date: 2006-10-19
forum: Desktop Environments
---

### Post by Tasu on 2006-10-19
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

Add this line to /etc/apt/sources.list

Then you can find in your Synaptic the new flashplugin-nonfree version 9 and even a flashplayer standalone.

Enjoy your yutube's perfectly synced! ^_^

Regards! ^_^

---

### Post by futsihoo on 2006-10-19
thanx alot :)

---

### Post by JoKo on 2006-10-19
Are you going to make a package for Edgy as well?

Thanks in advance!

---

### Post by TheSqueak on 2006-10-19
```
Fetched 3191B in 0s (4035B/s)
Reading package lists... Done
W: GPG error: http://3v1n0.tuxfamily.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
```

Any ideas?

I have downloaded the key and added it, it shows up in apt-key list

```
pub   1024D/81836EBF 2006-06-26
uid                  Treviño (3v1n0) <trevi55@gmail.com>
sub   4096g/EDD1E155 2006-06-26
```

---

### Post by hikaricore on 2006-10-19
good effort putting up a package file :)

sadly I already sshed to my box at home and did a wget/untar install hehe

oh well, back to work for me

---

### Post by damu on 2006-10-19
you can also install it in 2 clicks with [Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38") ;)

---

### Post by Lord Illidan on 2006-10-19
I tried this in Edgy by mistake.. worked just the same :) Thanks!

---

### Post by someguyouknow on 2006-10-19
The new flash works well except now i cant watch google videos.
at least in Opera... i havent tried firefox.

---

### Post by Treviño on 2006-10-19
I've made that packages ;)... They work also in edgy... 
So, if you've it and you don't want add my repo, read [this post]("http://ubuntuforums.org/showpost.php?p=1637953&postcount=13") to download the debs.

---

### Post by Tasu on 2006-10-20
Whops! Sorry for the person mistake... but I'm not the one that made the package (I should have had written it, sorry!)

Look at the URL in the repository string to find who made it!

---

### Post by Tasu on 2006-10-20
Aggh! ^_^ Answered too late! O_O Great job 3v1no! ^_^

---

### Post by Treviño on 2006-10-20
Thanks... :)
No problems... It's not so important the author... Just that people is using this resource ;)

---

### Post by yatt on 2006-10-20
Yay! Youtube has been bugging me lately for not having the latest flash.

---

### Post by Limulus on 2006-10-22
> **Treviño said:**
> Thanks... :)
No problems... It's not so important the author... Just that people is using this resource ;)

On my local LUG ML someone mentioned that the DEB didn't work for them because it conflicts with xfs <1:1.0.1-5 but Dapper's version (which they have installed) is 1:1.0.1-0ubuntu2

I don't happen to have xfs installed, so this wasn't a problem for me personally.

Any chance of this getting fixed soon?

---

### Post by bigbadsi on 2006-10-22
This works wonderfully.  No more sound sync problems.  Fantastic.

---

### Post by verbatim on 2006-10-22
> Fetched 3191B in 0s (4035B/s)
Reading package lists... Done
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

](*,) :-k 

I also have this issue.  Anybody know what is happening here?

Thanks in advance!

---

### Post by mellisa on 2006-10-22
```
W: GPG error: http://3v1n0.tuxfamily.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

```


I also had this little problem. If anyone knows how to fix it please let me know.:neutral:

---

### Post by Treviño on 2006-10-22
> **mellisa said:**
> ```
W: GPG error: http://3v1n0.tuxfamily.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

```


I also had this little problem. If anyone knows how to fix it please let me know.:neutral:
this:
```
gpg --keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9
gpg --export --armor 2D6CFB44DD800CD9 | sudo apt-key add -
```

should fix....

---

### Post by mellisa on 2006-10-22
Thanks for the quick reply. It worked great:D

---

