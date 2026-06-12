---
title: "Google Earth"
date: 2008-12-18
forum: General Help
---

### Post by josephmo on 2008-12-18
I downloaded Google Earth, and installed. The installation went fine, and the icon was installed in my Ubuntu Internet Group. When I started it, it gave me the following error message:

Google Earth detceted an error while trying to authrnticate. Please check the following:
-Your network connection (can you get to [www.google.com?](www.google.com?))
- your firewall settings (are you blocking /opt/google-earth/googleearth-bin?)

Error code: 29

Then the application does start, but most of the menu items are greyed out, and nothing appears.

As far as I know I do not have a firewall installed and configured, and obviously I can connect to the Internet, so there's nothing wrong with my networking connection.

Any ideas?

Thank you

---

### Post by squaregoldfish on 2008-12-18
Are you running 64-bit? If so, you need to install the lib32nss-mdns package.

Steve.

---

### Post by josephmo on 2008-12-18
> **squaregoldfish said:**
> Are you running 64-bit? If so, you need to install the lib32nss-mdns package.

Steve.

Solved the problem, thanks. I am experiencing a very interesting artifact though. Whenever I move the mouse away from the main image area, it turns into a scrambled mesh. It's as if the frame buffer for that window is filling with noise. This must be an ATI driver issue?

---

