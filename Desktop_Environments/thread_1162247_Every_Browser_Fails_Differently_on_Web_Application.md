---
title: "Every Browser Fails Differently on Web Application"
date: 2009-05-17
forum: Desktop Environments
---

### Post by skewray on 2009-05-17
I used to use the Discovercard Deskshop utility fairly often on Ubuntu 7 and 8, but with 9 I can't get Konqueror, Firefox, or Opera to function.  This cool tool generates a single-use credit card number, so it can't be stolen after the first use.  The page is [http://www.discovercard.com/customer-service/security/create-soan.html](http://www.discovercard.com/customer-service/security/create-soan.html) and click on the "Launch Now" button.  I don't know if the application is Javascript or Java or flash.  Each browser fails differently.

Konqueror shows a blank popup.  Actually, Konqueror has been doing this for most popups.

Opera never finishes loading the application.

Firefox creates the popup and the shows a cursive "f" button.  Clicking that shows a forward arrow button.  Clicking that shows the application, but typing into the password field just show what I type, so the application isn't really all there.

Any idea what the problem might be?

Brian

---

### Post by binbash on 2009-05-17
It is flash and works great on firefox 3.0.10

---

### Post by skewray on 2009-05-17
> **binbash said:**
> It is flash and works great on firefox 3.0.10

Aha!  So I have flash mis-installed at least two different ways.  I removed all of the open-source flash players from my system and re-installed Adobe Flash.  Now Firefox works.  The other two are still dogs.  Any suggestions on how I properly setup/reinstall a decent flash player for Konqueror and Opera?

Brian

---

### Post by binbash on 2009-05-18
When you install the flash player from the repository, it is also installed at Opera(i do not know the konqueror stuff) or if you are using adobe's installer you can define the path for opera at installer screen.

---

### Post by skewray on 2009-07-03
Except that reinstalling the flash player only fixed Firefox.  Opera still doesn't work.

---

