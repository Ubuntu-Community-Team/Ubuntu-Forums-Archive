---
title: "[HOWTO] Wolfenstein: Enemy Territory 2.60b on Ubuntu Studio 16.04"
date: 2018-07-01
forum: Gaming &amp; Leisure
---

### Post by kujaw2 on 2018-07-01
Here's how to install Wolfenstein: Enemy Territory 2.60b @ Ubuntu Studio 16.04. Should work for all Ubuntu forks.

It's an updated version of earlier [instruction for Ubuntu 15.]("https://ubuntuforums.org/showthread.php?t=2280340")



[LIST=1]
[*] Install Playdeb repository & package:
[LIST=1]
[*]In Software & Updates, Other Software tab, add repository:
```

deb http://archive.getdeb.net/ubuntu     xenial-getdeb games 

``` 
[*]Add the repository GPG key, open a terminal window and     type: 
```

wget -q -O-     http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add - 

``` 
[/LIST]
  
[*]Update your software list:
```

sudo apt update

``` 
[*]Install ET: 
```

sudo apt install enemy-territory enemy-territory-data

``` 
[*]Install necessary libraries to run 32-bit apps and have sound
```

sudo apt install libx11-6:i386 libxext6:i386 libstdc++6:i386 libgl1:i386 libsdl-sound1.2:i386

``` 
[*]Go to [https://etkey.org]("http://etkey.org"), download etkey and copy it to your ~/.etwolf/etmain/ directory.
[*]Run Wolfenstein: Enemy Territory. 
[/LIST]

---

### Post by mastablasta on 2018-07-04
i get no sound with ET on 64 bit 14.04. i wonder if i am missing the [COLOR=#000000][FONT=&quot]libsdl-sound1.2:i386 library  [/FONT][/COLOR]

---

