---
title: "skype not starting in lucid lynx"
date: 2012-04-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sathishgv on 2012-04-15
I recently installed skype using synaptic package manager. I m using ubuntu 10.04 lts. After the installation when i started skype from the internet folder, nothing happened. Then i went to the terminal and tried to start skype but i got the following error:
 "FATAL: cannot mix incompatible QT libraries 
Aborted"
Then i searched for the forums and tried various things nothing worked for me. Then in some thread i read that i shoud try the static version of skype available from skype website. I downloaded the files and i started skype from that folder and it worked. But every time i had to open the /usr/bin folder for accessing the skype. In the readme file it was given that the skype binary files should be copied to the /usr/bin folder and the other things such as sounds/, langs/ etc should be copied to the /usr/share folder.

What i did was i deleted the file skype from the /usr/bin folder and moved the skype from the static version folder. Now when i lauched the skype application from the internt folder it works. This may be a very simple solution (non-technical) but i thought of posting it because somebody may find this useful.

---

