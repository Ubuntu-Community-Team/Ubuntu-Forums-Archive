---
title: "how to turn off xgl in beryl?"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by mett on 2007-10-26
So in an attempt to retrieve my title bars, i right clicked on the beryl manager and clicked "force xgl". now any time i start beryl my pc hangs and i have to ctrl + backspace. I already tried completely removing beryl and reinstalling it and it still happens. is there any way i can turn off xgl through the terminal or anything else?

---

### Post by overdrank on 2007-10-27
> **mett said:**
> So in an attempt to retrieve my title bars, i right clicked on the beryl manager and clicked "force xgl". now any time i start beryl my pc hangs and i have to ctrl + backspace. I already tried completely removing beryl and reinstalling it and it still happens. is there any way i can turn off xgl through the terminal or anything else?

Hi when you remove beryl you will need to remove the setting manager also. Have you tried this command ```
sudo apt-get remover beryl beryl-manager
``` You may replace apt-get with aptitude if you prefer. Hope this helps.

---

