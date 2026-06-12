---
title: "Ubuntu running slow"
date: 2009-02-13
forum: General Help
---

### Post by Bubbie on 2009-02-13
I recently tried to dual-boot my new laptop:
[http://www.amazon.co.uk/Compaq-Presario-CQ60-107-15-6-inch-Sempron/dp/B001H9O20C](http://www.amazon.co.uk/Compaq-Presario-CQ60-107-15-6-inch-Sempron/dp/B001H9O20C)

But when I decided to install the new ubuntu it was running soo slowly that it wasn't nice to work with.

new windows opening slowly and stuff, even on the live cd it was going slow.

anyone knows how this can occurs? cause I think my laptop is good enough to have ubuntu running.

thnx

Bubbie

---

### Post by kanikilu on 2009-02-13
In my experience, Live CD's are generally slow because it's running of a CD that's constantly having to spin back up.

If it's installed on the hard drive, though, that laptop should be more than capable. I see it has a GeForce 8200M. Did you enable the NVIDIA driver in System > Administration > Hardware Drivers?

Also, do you have visual effects turned on? System > Preferences > Appearance > Visual Effects. If so, maybe try turning them off (select the "none" radio button) and see if that runs any smoother...

Although, it could have nothing to do with the graphics. You can check your memory usage by going to the command line (Applications > Accessories > Terminal) and run the *free* command.

---

