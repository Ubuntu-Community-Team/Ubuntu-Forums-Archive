---
title: "how can I stop shotwell from auto importing files on my HD"
date: 2012-11-24
forum: Desktop Environments
---

### Post by lister171254 on 2012-11-24
Appreciate if somebody could tell me how can I stop shotwell from auto importing files on my HD.

I only want it to import files from directtoies I chhos, not the entire disk.

I've completely un/resinstalled shotwell, but the first thing it does is to import every media on my HD.

Thanks

---

### Post by RoosterHam on 2012-11-24
when you first start shotwell, it asks whether you would like to import photos. unselect the check box and check 'the don't ask again.'

if it's already done go to the Edit>Preferences menu selection, and import is the first options on the first tab... you can choose folders and import options.

does that help?

---

### Post by lister171254 on 2012-11-25
I think it's pulling all media files in when I enable the **Watch library diretory** (see screenshot)

I would expect it to only watch the folders I imported, but it seems to pull in everything on my HD

---

### Post by RoosterHam on 2012-11-26
shotwellLib is a subdir in your ~/? (my experience of shotwell has been exactly as you assume it should be, so my train of thought is way out there with this one...)

---

### Post by lister171254 on 2012-11-26
Yep. So not sure why it works for you but not for me

Just went back in and enable to watch the library. Mind you, that subdir is empty

---

### Post by eric-yorba on 2012-11-26
Shotwell has a bug where if your library photo can't be found, it looks in the parent folder.  So if there's some kind of issue accessing that folder (path is incorrect, permissions are set wrong, etc.) then it may be looking in a parent folder.

---

### Post by Shuudoushi on 2012-11-26
You should also make sure there isn't a typo in the path. I made the **very** noobie mistake of having a simple typo in the path names and it drove me crazy for a week >.>

---

