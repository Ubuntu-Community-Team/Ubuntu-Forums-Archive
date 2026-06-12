---
title: "problem with dual monitor set up"
date: 2009-04-15
forum: Desktop Environments
---

### Post by mr_gourami on 2009-04-15
so i have been trying for two days to get this to work. i am not sure what i am doing wrong. 

Goal -- Have my computer use two monitors. Each monitor is a seperate desktop not a clone

Equipment -- Hp laptop dv6000 model 6119us Ubuntu 8.10 nividia geforce 6150


What i did

1. ubuntu restricted drivers, Update nvidia driver to 180 (most recent)
2. pres alt+F4 (for hp laptop if i press it twice i get both screens to work but as a clone of each other.
3. open X server
4. under x server display config
   1. i make each model seperate x screen
   2. enable xinerama
   3. set each monitor position one above and another below 
   4. Save config file 
   5. click apply ( i get a warneing "cannot apply"
                   @location of x screen has changed
                   @ location type of x screen has changed
                   @color depth of an x screen has changed
                   @ an x screen has been added or removed
   6. click apply what is possible

computer flashes and then i get only one screen, the other one is just gone... 
 so i restart and then i get a big thing about how its not supported and i have to revert to the default set up... i dont get it. 

am i skipping something? Am i doing something wrong? too many steps at once?



      .

---

### Post by mr_gourami on 2009-04-18
i was able to fix this thing somewhat. i cant get a true dual view but it seems to work under a vertical span. i dont get seperate backgrounds but each is a seperate screen. i give up on trying to get it to work better.

---

