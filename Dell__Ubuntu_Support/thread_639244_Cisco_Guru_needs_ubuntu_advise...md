---
title: "Cisco Guru needs ubuntu advise.."
date: 2007-12-13
forum: Dell  Ubuntu Support
---

### Post by mtp337 on 2007-12-13
Aloha All,

I am striving to be free of windows, and I have been doing it ok for about 2 months on my 1420 from dell with ubuntu pre installed!  

However I live and die by my laptop, being a self employed Cisco  network consultant.  90% of the time I can do this windows free, but 10% of the time I get snagged and I need to run a windows application.  Most of the time I can just remote to a windows machine, but sometimes I cannot. 

I think I have 2 options.

1 setup the laptop to dual boot
2 virtualize xp in ubuntu?
3 wine 

I am leaning towards option 1 because its the most likely to solve any issues, but would really like to know if 2 available and where to start.  Wine is ok for some things, but can't do 100% of what I need.

Mahalo in advance for any help!

:)

---

### Post by markusf21 on 2007-12-13
for # 2 try out [_[COLOR="Navy"]vmware server[/COLOR]_]("http://www.vmware.com/products/server/") works well and it's free. I just checked and the latest version is in the gutsy repos

---

### Post by rickyjones on 2007-12-13
I would go with either option 1 or 2. If you are totally striving to be Windows free then I would try virtualization first - unless part of the problem is using a serial cable to connect directly to the device. But if all you are doing is needing to run the Cisco applications over the network then I would virtualize.

Hope it helps!

-Richard

---

### Post by Mach1US on 2007-12-16
I'm working on cisco certification myself and was in the same boat for a while too.
Currently i got dual boot just to have a bulletproof setup but i definitely highly recommend VMware server which i have been using for a while and is great for many other reasons like server virtualisations or running simple appliances doing little nifty tricks like DNS with virtually no overhead .
My sugestion would be tho have dual boot but primarily rely on visualization. 
I'm using minicom and gtktem for console sessions , what do you prefer or use yourself ?

---

### Post by Mach1US on 2007-12-16
.

---

