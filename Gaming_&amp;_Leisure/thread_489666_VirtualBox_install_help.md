---
title: "VirtualBox install help"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by Jockboy98295 on 2007-07-01
I installed VirtualBox through Ubuntu's automatic install program (i cant remember what its called, sorry), seems like a great program.  But i found it didn't install  libxalan-c and libxerces-c and need some help finding and installing both.  I also am unable to add the Innotek public key to my sources.list, it has the repository but will not download from it.  I am currently running Ubuntu 7.04 Feisty Fawn x386 on a 64 bit AMD and I installed VirtualBox 1.4.0. I am kinda new to Ubuntu, so please be "gentle" :)

Thanks

---

### Post by tgm4883 on 2007-07-01
If you used synaptic to install virtualbox then it is downloading from the virtualbox repos as virtualbox isn't in the Ubuntu Repos

---

### Post by Jockboy98295 on 2007-07-01
I used GDebi Package Installer because i didnt want to download it to my desktop

---

### Post by tgm4883 on 2007-07-01
Did you download the key then add the key from the same directory using ```
apt-key add innotek.asc
```

You might have to sudo that

---

### Post by Jockboy98295 on 2007-07-01
i tried to download the key from the virtual box web site, but it will not let me download it.  It just brings the key up in a different window.  I have tried to add the key through synaptic, but it requires that i download a key specific file, so it wont work either.  I tried apt-key add innotek.asc like the VB website says but of course nothing just this error 

logan@logan-desktop:~$ apt-key add innotek.asc
gpg: can't open `innotek.asc': No such file or directory

When you sudo it the same error occurs.  

I also tried to add the key via a web site like this

 wget -q [http://www.virtualbox.org/debian/Innotek.asc](http://www.virtualbox.org/debian/Innotek.asc) -O- | sudo apt-key add -

but you get this error 

gpg: no valid OpenPGP data found.


not sure what  to do. :(

---

### Post by Jockboy98295 on 2007-07-01
ok tried it again this is what happened


logan@logan-desktop:~$ wget -k [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) -O---15:23:04--  [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)
           => `-'
Resolving [www.virtualbox.org](www.virtualbox.org)... 88.198.19.108
Connecting to www.virtualbox.org|88.198.19.108|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,706 (1.7K) [text/plain]

 0% [                                     ] 0             --.--K/s             -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.6 (GNU/Linux)

mQGiBEZkBn8RBACccOdQohVvrpVvgBx2F8j1fv+0UwzGwyVFhGzUNBUIClsLQEMf
jFAspPFUsndzzCnotrFJpKc5ES/Lf9Yt2LuVr3bsUB8kF6AEJTuBdapwiQIXH72M
80MRhFLquuCDXS8RFvMmhXxmjpTUchOWpFNH4CC9FQNuoMBqUPJovYaLLwCgwbAV
1+2328/lcXkO5uC8mZN9KJUEAI7ZUJZeAqrnptCyha8sZf8UUkFh6AGMJPxafK1z
cis65BOFXYyq8G2qhPKqSFPAUAfjb7E7ONK1kMcMfPE1dKFE1bZ//pjjHzUds6/y
UP1LeuYveWnIQmsGv3+OkfUovVDc4BdyIGMruPu4VBy0FyefTjf47Am4D69LZ9Wz
+IrSA/9GXrzzJkn0sfHtXo3ihIhZzZtZGYsNaLqF9pb0Pk/6SeBq3EgTBGIuSFdj
HemwbaPrb7WzGKEZcaRNzrgfx13uQbsQoCJM9XTr5I37+nA8UkibcuXyPKEgSBNt
I+jx9Cv6+86ivc0Dx8kExauoSE1rWksFwhk+VscaMzezkfe1U7Q0aW5ub3RlayBH
bWJIIChhcmNoaXZlIHNpZ25pbmcga2V5KSA8aW5mb0Bpbm5vdGVrLmRlPohgBBMR
AgAgBQJGZAZ/AhsDBgsJCAcDAgQVAggDBBYCAwECHgECF4AACgkQOQ7D/5J8zHNV
ngCgnzBMPLtVSP7U0988Q4A03XjYjg0An3wHt385u1hAXBgCIWA4J/WQOGIluQIN
BEZkBoEQCAC7eZCkCrT0ZNAgqIHv3SUxieqiMMNDfMsrwHO1cdO0zuMkcGDRDENE
sNbqdvL9TRWBb/ub0gcl3bFATihAP68tssqFMv9fsHIFK7y9obS5vRUUi2NJKAMv
XTxmYcBlXnEBLfpJR1Vct60+dcmkF0cgMm8m5BhjLt8aAPUUsDvZo/yUMVYbV+4s
ulKPw2h7nubsHUPb+0pVNHyzJlWt1On0jW5t3XF8En9m3f0PWlmBJOnaZOb0cLrB
Om6qiKK+a7ps0jf/2047Kkto1rToEAlut+KwwQaLQxPcI7jRirDZ+4nYgQJGiQLL
PHPSOVNwRDw/AS8X2Q6CxqjeZCXRuqUHAAMFB/9Vn6psB1appyYZS7p+2bsChnjv
NyA9SAVRAMHfhDXNiD1EHEExedP/KgIBGMUSwrc8g/8IqdwFIPUPueIEt2PkbI5i
zR8ADdW3tkgKnBI/3hxin2r9osvpNZUJsqamPpmth5G07Oj/MGtFgL8aLqXN8hIP
L1CrcvWnAsizIC+/RzqHZQVYkVWh7/Z7Vt321H+1fqTpTAs1VLKIcruCrVBMW5Kh
568Zla8r+EvrLPTLvdOtabDuhsYnyqWEWJfiiSlTB+Wm1nilTKz9r1qDikOsM51O
f4vobGqYLJrlW4dx3XA7yDhmTQwLTG48fh/3ORQoxCp4z+sHwDPIXeH3g7PUiEkE
GBECAAkFAkZkBoECGwwACgkQOQ7D/5J8zHMU2wCgusNPxQhdlszpi2vvFHoRL67+
2kgAnRvA99DMrSFPDALce3Rx0lXGlImA
=Ow4f
-----END PGP PUBLIC KEY BLOCK-----
100%[====================================>] 1,706         --.--K/s             

15:23:05 (160.34 MB/s) - `-' saved [1706/1706]


Then i tried to add it with the "apt-key add Innotek.asc" it says it dosent exist.  Could it have saved it as something else, or am I doing it wrong?

---

### Post by tgm4883 on 2007-07-01
right click on it and say save as

---

### Post by Jockboy98295 on 2007-07-01
I'm in the terminal,  that option is not given.  
 
However i just got it to work by inputting this code

logan@logan-desktop:~$ apt-key add innotek.asc  | wget -k [http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc) 
 
However i still do not have "libxalan-c" or "libxerces-c".  Do you know where i can get them?
I tried updating VB but it did nothing and these files are not listed in synaptic or add/remove.

---

### Post by tgm4883 on 2007-07-01
sudo apt-get install libxalan-c libxerces-c libstdc++

---

### Post by Jockboy98295 on 2007-07-01
when i run that command it says it cannot find libxerces-c, libxalan-c
I have libstc++6 installed

Where can i find these?

---

### Post by tgm4883 on 2007-07-01
did you sudo apt-get update after adding the new repo?

---

### Post by Jockboy98295 on 2007-07-01
I finally got those files to install, and update. They were labeled with version numbers (duh) so they didnt look correct, and didnt match what i typed in.  I had tried the apt-get update.  
Now i'm trying to figure out how to put myself into the vboxusers group, the documentation is not very clear.

---

### Post by tgm4883 on 2007-07-01
system > administration > users and groups

---

### Post by Jockboy98295 on 2007-07-01
I cant believe i didn't think of that!!

why would i get this warning when i start VB from the terminal--

logan@logan-desktop:~$ VirtualBox
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device

VB still opens and it seems like everything is operating just fine, but i dont really like to see errors, unless this is something i need not worry about.

---

### Post by tgm4883 on 2007-07-01
Don't know, 1.4 is still a little buggy.  I get that error too

---

### Post by Jockboy98295 on 2007-07-01
OK
Thank you for your help, and patience.
I'll inform you of any problems when i actually get XP installed on it.  I currently only have an upgrade disk and no other operating system to show that i had a different win OS installed. 
Good luck :)

---

