---
title: "Ripping encrypted DVDs"
date: 2005-11-20
forum: Desktop Environments
---

### Post by rado_london on 2005-11-20
Hi all
I have a problem. I have HP Pavilion dv4000 and I have DVD rom. Yesterday I went and rent a DVD from my local Blockbuster. I downloaded the dvd::rip program. But it doesnt rip any encrypted files. Do you have any ideas?

Best Regards:)

---

### Post by etc on 2005-11-20
Don't rip dvds you own because it's illegal.

For the dvds you do have, download the libdvdcss package from the VLC developers site (search google because I'm not sure if it's okay to link it here), then do a 
sudo dpkg -i libdvdcss*

---

### Post by regeya on 2005-11-20
[QUOTE=rado_london]Hi all
I have a problem. I have HP Pavilion dv4000 and I have DVD rom. Yesterday I went and rent a DVD from my local Blockbuster. I downloaded the dvd::rip program. But it doesnt rip any encrypted files. Do you have any ideas?

Best Regards:)[/QUOTE]

As was said above, don't steal movies.  A real bugger of a problem is that the same software that allows ripping of DVDs is also needed to allow playing of DVDs.  Both uses, AFAIK (though IANAL) are illegal, though.

However, if you're of the same opinion as me, you know you've got a drive, which shipped with licensed software that won't work on your operating system and want to watch movies on your monitor, since the monitor is likely higher-res than your TV.  If so, take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

HTH

---

### Post by manicka on 2005-11-20
To obtain libdvdcss2

[http://doc.gwos.org/index.php/PLF](http://doc.gwos.org/index.php/PLF)

---

### Post by bionnaki on 2005-11-21
I never liked dvd:rip.
I recommend dvdbackup instead - it's a commandline program.

---

### Post by Breepee on 2005-11-21
It's perfectly legal overhere. And I think if ripping is illegal in your country, using libdvdcss probably is illegal too.

---

### Post by jnie on 2005-11-21
[Enable the universe and multiverse repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

sudo apt-get install libdvdread3
sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

Worked for me.

Jan

author of
[Venture into the LinuxWorld]("http://intothelinuxworld.blogspot.com/")

---

