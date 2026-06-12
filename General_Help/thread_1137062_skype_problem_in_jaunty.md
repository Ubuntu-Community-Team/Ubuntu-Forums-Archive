---
title: "skype problem in jaunty"
date: 2009-04-25
forum: General Help
---

### Post by cmay on 2009-04-25
hi.
i have been using skype for as long as i had my new laptop which is 2 or 3 month on ubuntu 8.10 with out any problem and i use it everyday. 

but after upgrading to jaunty i got a problem that i dont know how to fix. 
what happens is that i connect and skype is sucking a lot of cpu and when i talk with my brother sound stops working and it happens after a short period of time.  

i have to xkill skype to shut it donw and start over starting skype and log in  to continue convertion. 

i noticed if i start firefox it happens often at the same time.

anyone got an idea what the cause of this is. 
thanks for the time.

---

### Post by gaurab on 2009-04-27
Exact same problem here.

---

### Post by cmay on 2009-04-27
i had found a page in which ther was a mention of it being a known bug in skype but i did not get it bookmarked even thought i did. 

i think that it mentioned a fix that was about setting the startup settings on skype in anohter way but i cant find the link or page again.

---

### Post by mfarewell on 2009-06-17
This bug is mentioned all over the place e.g.: [http://forum.skype.com/index.php?showtopic=306381&st=20]("http://forum.skype.com/index.php?showtopic=306381&st=20") I have tried most of the suggested fixes but it still doesn't work. I can talk for a few minutes but then suddenly it all goes quiet and a cpu core is at 100%, have to kill skype to get it going again and then the same thing happens. Has happened ever since I updated to Jaunty from intrepid (which I regret doing).

---

### Post by PGScooter on 2009-06-17
I had this problem. I installed skype-static-oss from the medibuntu repository and this fixed it. I would suggest trying that as well as skype-static. I think you need to remove your previous skype installation. But the versions to me looked exactly the same and even had all of my contact information stored! (to remove, I used the command ```
sudo apt-get remove skype
```. Post back with what you figure out. Good luck!

---

