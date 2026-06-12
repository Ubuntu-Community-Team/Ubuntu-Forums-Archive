---
title: "sh files not working"
date: 2005-11-28
forum: Desktop Environments
---

### Post by shade11 on 2005-11-28
I tries to install xmms and wine but after I cd the directory and type in./configure it gives me an error message. I cant use the apt get feature (Because of no internet) what do I do?

---

### Post by earobinson on 2005-11-28
what error message do you get.

Also post a ls -la so we can see the permisions on the file

---

### Post by chronusdark on 2005-11-28
you realize that both wine and xmms are in the breezy repos right? why noy just use synaptic?

my bad i should have read the whole post....you could just get the .debs of them tho and use dpkg -i <.deb file here>

---

### Post by earobinson on 2005-11-28
[QUOTE=chronusdark]you realize that both wine and xmms are in the breezy repos right? why noy just use synaptic?

my bad i should have read the whole post....you could just get the .debs of them tho and use dpkg -i <.deb file here>[/QUOTE]
that should work also

---

### Post by shade11 on 2005-11-28
Where do I get it. btw I had changed the permissions before so everyone can read write and execute.

---

### Post by benplaut on 2005-11-28
[QUOTE=shade11]Where do I get it. btw I had changed the permissions before so everyone can read write and execute.[/QUOTE]

hey Ian...

If you don't have internet (get me at school, i might be able to get your wifi working), then you'll first need to get build-essential, which contains many compilers and dev tools needed to compile from source

Seriously, ubuntu isn't made for installing everythign from source 'cause you have no internet - if you want to use linux, you pretty much have to have internet, or use debian, which includes 16000 packages on 26 CDs ;)  (no, that does *not* mean that you should go of and try to install debian!)

Good Luck!

---

### Post by shade11 on 2005-11-29
Ok. Well I will have to try and find some sort of internet access. I mean is there something that can help me install from source?

---

