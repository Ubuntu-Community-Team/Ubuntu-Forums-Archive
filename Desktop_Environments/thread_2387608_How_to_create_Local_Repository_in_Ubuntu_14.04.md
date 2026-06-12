---
title: "How to create Local Repository in Ubuntu 14.04"
date: 2018-03-21
forum: Desktop Environments
---

### Post by giobaxx on 2018-03-21
Just to start to playing with Ubuntu Repository i wanted to try to use my UBUNTU DVD as Local Repo. Googling what i did was

1) Mount the ISO for example in **/mnt/localRepo**
2) in the source.list i put the the following string: [I][B]deb file:/mnt/localRepo trusty main restricted

[/B][/I]but it does not work, could you tell me what i miss?

Apart Mirroring the Repo, there is a way create an updated Repository from an Updated System?


Tanks a Lot

Joe

---

### Post by Frogs Hair on 2018-03-21
This the only official documentation I find for an offline repo .

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by Tadaen_Sylvermane on 2018-03-21
Not sure why you would want a full repo mirror. For my use I found an apt-caching server more effective. Only mirrors the packages that I actually use. Download once and they are local for any other system on my lan that needs them. Simple to set up. Look for apt-cacher-ng

---

### Post by giobaxx on 2018-03-25
Sometimes i would need to update system that cannot be connetcted to the network, and would be usefull to perform at least some updates, but also i would like to learn more deeply how the ubuntu repo works. 

I saw the structure of the file ***source.list*** that should be like this [I]**[COLOR=#0000ff]deb [/COLOR][[COLOR=#0000ff]http://archive.ubuntu.com/repo[/COLOR]]("http://archive.ubuntu.com/repo")[COLOR=#0000ff] distribuition component1 component2 component3[/COLOR]**[COLOR=#0000ff]
[/COLOR][/I]
then i found this **[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)** that is about how to build a personal repo where in the source.list there is a line like this: [B][COLOR=#0000ff]deb file:/usr/local/mydebs  ./

[/COLOR][/B]In ***mydebs ***i have copied all my packages but what it means "[COLOR=#ff0000]**./**[/COLOR]"? at the end of the line. There is not component? ....is that instead of the component [I]main restricted...etc.....

[/I]That brings me other questions which is the correct structure/folder of a repository?

When i tried to use my dvd as repo i have mounted the iso and i used the root of mounted dvd as repo(***deb file:/mnt/localRepo***) even if the folder straucture seems to be a bit different from the one   provided on internet by canonical.

I would like to understand all this things in order to mange repo best as i can...

---

### Post by cruzer001 on 2018-03-25
> Sometimes i would need to update system that cannot be connetcted to the network

Thats different from creating a local repository.

[https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+update+a+off+line+machine+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=how+to+update+a+off+line+machine+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by giobaxx on 2018-04-03
Tanks great!!!

---

