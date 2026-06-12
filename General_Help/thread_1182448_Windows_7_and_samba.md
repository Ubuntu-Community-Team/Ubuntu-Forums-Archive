---
title: "Windows 7 and samba"
date: 2009-06-09
forum: General Help
---

### Post by arsenik on 2009-06-09
I recently installed Ubuntu 9.04 and followed the how-to on installing Samba.  I shared a directory called "My Files" and have used vista to connect to \\192.168.1.112\MyFiles and it works great.

However, when I try to connect with Windows 7 it asks for a username and password.  I've tried many username/password combinations and nothing works.

I google'd the problem and tried the following solution with no successful results:
> 
1. In Vista, open the Control Panel
2. Switch to "Classic" view
3. Double-click Administration Tools
4. Double-click Local Security Policy
5. Or Secpol.msc
6. Expand "Local Policies" and select "Security Options"
7. Alternate : Type secpol.msc to get editor up then
8. Locate "Network Security: LAN Manager Authentication Level" in the list and double-click it.
9. Change the setting from "Send NTMLv2 response only" to "Send LM & NTLM - use NTLMv2 session if negotiated"
10. Network Security: Minimum session security for NTLM SSP Based (including secure RPC) Clients
11. Change the setting from "require 128 bit" to unchecked (No Minimum)
12. Click OK


Any help is appreciated.

---

### Post by probain on 2009-06-29
My suggestion is that you haven't set up your actual samba-users. This is at least if your logging in with pre-existing user acounts on your machine.

Try adding/mirroring a user with:
```
smbpasswd -a USERNAME
```

---

