---
title: "All my disk space got used up suddenly - df misreports space"
date: 2008-12-04
forum: General Help
---

### Post by AussieGuy69 on 2008-12-04
i was editing a text file when suddenly, something mysterious used up all my parition space.

/dev/sda3             45718980  36407116   7007744  84% /

df is misreporting the amount of space used on my partition. Ive done a full "properties" of the / folder in nautilus running as root with sudo, its counted everything totalling 11GB. 


df -h says this however....  /dev/sda3                 47GB      38GB       8GB  84% /       in other words 8GB free of 47GB, in other words theres alot more space being used up by something, that the full file count of the / folder that nautilus did could not see.

df without -h says /dev/sda3             45718980  36407784   7007076  84% /

What could be causing the inconsistency there? I noticed this problem when gedit would not let me write a text file for "lack of space". I quickly deleted a few big files to free 6gb to maintain system stability but the result is above.

What could be causing this amount of space to be used up and how do I get the space back?

Ive just rebooted the machine and the space is still mysteriously all used up, as above.

---

