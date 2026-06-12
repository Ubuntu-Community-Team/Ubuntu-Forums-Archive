---
title: "HOWTO: Tamil Keyboard on Ubuntu 6.06"
date: 2006-10-03
forum: Desktop Environments
---

### Post by swamytk on 2006-10-03
Enabling Tamil input method on Ubuntu Linux 6.06 LTD (Dapper Drake) is so sweet and simple. Here is an HowTo on that. It involves three steps:

**1. Enabling Extra Repositories:**

    * System -> Administration -> Synaptic Package Manager
    *
         a. Settings -> Repositories
         b. In the Installation Media tab, click Add. There are three separate repositories; Dapper Drake, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes
         c. You should now see those three repositories under Channels. Make sure Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse) appears under each repository
         d. To refresh the list of known packages (equivalent to apt-get update)
         * Edit Menu ->Reload Package Information

**2. Installing Tamil Fonts**
Search for following packages in Synaptic Package Manager and install the same with all dependencies:

         * ttf-tamil-fonts

**3. Installing SCIM Input Method**
Search for following packages in Synaptic Package Manager and install the same with all dependencies:

a. scim    b. scim-gtk2-immodule   c. scim-tables-additional

**How to type in Tamil:**
1.  Open Gedit Editor through Applications -> Accessories -> Text Editor.
2. Right-click at Text area, select Input Method -> SCIM Input
3. You can notice a small toolbar at the bottom right of the screen. Select Tamil Keyboard layout from the menu on that toolbar.
4. Start typing in the text editor. You will get Tamil characters.

Happy editing hours with Tamil. Let us take Tamil to next generation!

Here is my blog posting on this: [http://cutecomputer.wordpress.com/2006/10/03/howto-tamil-keyboard-on-ubuntu-606/](http://cutecomputer.wordpress.com/2006/10/03/howto-tamil-keyboard-on-ubuntu-606/)

Note: I don’t have access to Ubuntu right now. So any correction and omissions on this posting is welcome.

---

### Post by amachu.techie on 2006-10-18
Good job. Welcoming you to Ubuntu Tamil Team.

URL: [www.ubuntu-tam.org](www.ubuntu-tam.org)
wiki: [https://wiki.ubuntu.com/Tamil](https://wiki.ubuntu.com/Tamil) :)

---

