---
title: "Stopping an active software RAID-1 setup"
date: 2009-01-02
forum: General Help
---

### Post by summersab on 2009-01-02
Alright, so I've googled and googled. No good. I have my Ubuntu set up on 2 mirrored drives using software RAID. I'm attempting to shift a few drives around, and I basically need to break my RAID-1 setup WITHOUT destroying the ability to boot. However, if I do madadm --stop, I am told that the device is busy. Well, yes - this is true. It is busy, mounted, and it is my main active partition. Obviously, if I restart to a boot CD, the RAID isn't present since it is system-dependent. So, how do I break this active array without crippling my system? Thanks!

---

### Post by fjgaude on 2009-01-02
Well, using a liveCD you could install **mdadm** and go from there. I've done it. Just use apt-get install mdadm, and there you have it. Ready to do what you wish, which I'm not sure what that is. <smile>

---

