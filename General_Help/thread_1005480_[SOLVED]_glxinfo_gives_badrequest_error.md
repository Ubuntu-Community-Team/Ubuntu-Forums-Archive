---
title: "[SOLVED] glxinfo gives badrequest error?"
date: 2008-12-08
forum: General Help
---

### Post by sdowney717 on 2008-12-08
scott@scott-desktop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
scott@scott-desktop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
scott@scott-desktop:~$

---

### Post by sdowney717 on 2008-12-08
SOLVED by reinstalling all FGLRX packages in synaptic

---

