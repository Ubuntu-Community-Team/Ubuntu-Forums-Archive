---
title: "ubuntu startup sound"
date: 2005-10-23
forum: Desktop Environments
---

### Post by kreso on 2005-10-23
I removed the startup sound in System->Prefferences->Sound and it still plays it after login???

---

### Post by mabaw on 2005-10-23
I have the same problem, and it also applies to the logout sound.
A temporary fix might be found with :
sudo chmod 600 /usr/share/sounds/startup.wav (for the login sound)
sudo chmod 600 /usr/share/sounds/shutdown.wav (for the logout sound)

---

