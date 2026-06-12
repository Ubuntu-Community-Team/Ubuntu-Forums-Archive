---
title: "Things that I would like to improve for better user experience"
date: 2009-06-12
forum: General Help
---

### Post by yanivfr1 on 2009-06-12
Hi All,



As a Windows user for more then several years (Or as long as I remember my self) I didn't experience such a good OS like Ubuntu.



Although I got some ideas how to make the user experience even batter.

1.The &#8220;File system&#8221; is to much exposed, Sometimes I'm going lost (Sorry, but I'm a newbie).
To much  folders that I'm not going to use (Maybe in the futures when Ill be a pro).
I know that I can go directly to my Home folder, But it also located in the &#8220;File system&#8221;.
I would like that &#8220;Simple User&#8221; will got directly to his files with out being present in the File System folder. (Maybe I'm not fully understand the Linux file system order).

2.I want more control on my system with out using a Terminal console.(As a Windows user I barely use the Command prompt. (I'm not a programmer or a computer since guy).

bye  till the next time I got  something to complain about something

---

### Post by donkyhotay on 2009-06-12
> **yanivfr1 said:**
> 
1.The &#8220;File system&#8221; is to much exposed, Sometimes I'm going lost (Sorry, but I'm a newbie).
To much  folders that I'm not going to use (Maybe in the futures when Ill be a pro).
I know that I can go directly to my Home folder, But it also located in the &#8220;File system&#8221;.
I would like that &#8220;Simple User&#8221; will got directly to his files with out being present in the File System folder. (Maybe I'm not fully understand the Linux file system order).

2.I want more control on my system with out using a Terminal console.(As a Windows user I barely use the Command prompt. (I'm not a programmer or a computer since guy).


1. the filesystem is designed the way it is intentionally to keep things organized based on the type of file it is. This makes more sense when you're used to it rather then dumping everything in 'program files' or the windows directory. With normal usage there is no need to access anything outside of the home directory. If you don't know what you're doing outside of home and are getting lost you have no business being there, unless of course it's at the direction of someone who knows what they're doing and then you're not really lost since you're just following instructions.

2. the CLI is *much* easier for fixing problems then any GUI if you don't know what you're doing. An example of this is if someone reports some file is reporting a permissions error. Here are the instructions for fixing that with the GUI:

open nautilus
find the file
right click on the file
click on the permissions tab
make certain that user is set to 'read/write'
make certain that group is set to 'read/write'
make certain 'allow file to execute' is checkmarked
click ok

as compared to:

copy/paste the following into the terminal
```

chmod 777 ./somefile

```

Seriously, for someone that knows nothing about computers and just wants it work, which set of instructions are going to be easier to follow and much less likely to cause problems? I'm not saying your opinion is wrong, it's just an opinion. But linux is designed for ease of use and doesn't obsfucate anything like most other OS's do. Sure some things are easier to do with a GUI which is why GUI's were developed but there are *many* things easier to do with the CLI and linux keeps it around because of that.

---

### Post by kerry_s on 2009-06-12
1. i understand your use to windows were it's common to hide the system from the user, in linux you are in charge & are trusted that you can learn right from wrong, so theres no need to hide anything.

2. you can already do that, a lot of people just enjoy using the terminal, it's a much simpler thing.

---

