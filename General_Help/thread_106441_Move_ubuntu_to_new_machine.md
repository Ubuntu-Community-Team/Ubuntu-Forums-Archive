---
title: "Move ubuntu to new machine?"
date: 2005-12-20
forum: General Help
---

### Post by bigblop on 2005-12-20
I have installed Ubuntu on my home PC. Now I am planning to take the HDD where I installed Ubuntu and move it to another machine.

Will this work or do I need to make a completly new installtion of Ubuntu on the new machine?

---

### Post by Gandalf on 2005-12-20
This will work but i think you might face some problems about Devices, you can try to reconfigure them, i bet you might want to
sudo dpkg-reconfigure xserver-xorg

Good luck

---

### Post by Rackerz on 2005-12-20
[QUOTE=Gandalf]This will work but i think you might face some problems about Devices, you can try to reconfigure them, i bet you might want to
sudo dpkg-reconfigure xserver-xorg

Good luck[/QUOTE]

Yeah it'll be similar to trying to do the same thing with Windows. Except Windows wont boot Ubuntu probably will. It will work just run sudo dpkg-reconfigure xserver-xorg as said above.

---

