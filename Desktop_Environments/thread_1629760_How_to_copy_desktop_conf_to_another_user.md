---
title: "How to copy desktop conf to another user?"
date: 2010-11-24
forum: Desktop Environments
---

### Post by ziazis on 2010-11-24
Hey guys,

like in the title my problem - i don't know how to copy the config of a desktop (like with all the icons on it) to another user.

I've tried to copy the ../.kde/share/config/plasma-desktop-appletsrc

but that didn't succeed :(...

So i wanna ask is there a possible way to do so?

I'd appreciate any help :)...

Cya Ziazis

---

### Post by ankspo71 on 2010-11-24
Hi,
I think it is an ownership problem. The file might be ignored because the user does not have permissions to use the file. Try changing the ownership of the config file so that the other user has ownership of it - immediately after you copy it over to the other user. Here is how you can do that in the terminal.

```
sudo chown username:username /home/username/.kde/share/config/plasma-desktop-appletsrc
```
Be sure to replace "username" with the other user's name. You can also use userID:groupID instead... which is required in some Linux distributions.

Have you already tried copying the entire ~/.kde (/home/yourname/.kde) folder over to the other user account? This would copy all KDE related settings, including downloaded KDE themes, KDE desktop settings, KDE application settings, etc. Also, like I said, I think you will have to change the permissions (ownership) of the files afterwards, so the other user will have permissions to use them. But be aware that this will copy KDE related passwords for kopete, quassel, rekonq, konqueror, etc, so it is best to remove those passwords first.

Hope this helps.

---

### Post by ziazis on 2010-11-24
> **ankspo71 said:**
> Hi,
I think it is an ownership problem. The file might be ignored because the user does not have permissions to use the file. Try changing the ownership of the config file so that the other user has ownership of it - immediately after you copy it over to the other user. Here is how you can do that in the terminal.

```
sudo chown username:username /home/username/.kde/share/config/plasma-desktop-appletsrc
```Be sure to replace "username" with the other user's name. You can also use userID:groupID instead... which is required in some Linux distributions.

Have you already tried copying the entire ~/.kde (/home/yourname/.kde) folder over to the other user account? This would copy all KDE related settings, including downloaded KDE themes, KDE desktop settings, KDE application settings, etc. Also, like I said, I think you will have to change the permissions (ownership) of the files afterwards, so the other user will have permissions to use them. But be aware that this will copy KDE related passwords for kopete, quassel, rekonq, konqueror, etc, so it is best to remove those passwords first.

Hope this helps.


Hey ankspo71,

thx for your reply.

I also thought of the ownership problem but it didn't help at all :)... Because if i use the config it is "used". The only problem at this point is - it still doesnt show me my wallpaper neither my icons that are in the config. (I've also watched the paths they're correct)

I've also tried do diff the files if i get a new icon on the other desktop (on the one i copied the file) and i saw that it just put some new [containments][xx] etc... dunno exactly how its named at the moment :).
It also renewed the wallpaper part into the default one...

Well however i don't think it's a ownership problem.

Any other ideas? (I don't have the old .kde folder anymore <.<... - should have tried it earlier on a trash user, dammit...). But anyway i'll try this method with another .kde folder.

---

### Post by ziazis on 2010-12-06
Hey guys,

i got the solution a while ago but didn't come to write it here ;).

Just copy the file 

/.kde/share/config/plasma-desktop-appletsrc

into the /etc/skel folder. (with all folders that are listed, that means, create in /etc/skel

/.kde/share/config folders and than copy the plasma-desktop-appletsrc)

Of course u will need to do it !before! creating your new user, but anyway that will do it ;).

Cya Ziazis

---

