---
title: "Fingerprint scanner locked me out"
date: 2015-07-04
forum: Desktop Environments
---

### Post by shailesh_paranjpe2 on 2015-07-04
I know there is already a thread with this name but it is not useful to me.  I made some wrong changes to common-auth file and the system is not allowing me to login now. I could not succeed in reversing the changes made to this file by dropping to shell root since the system is saying that the file is read only even after using sudo command. 
I am also not able to edit this file using a USB based ubuntu,  again the file is read only. 
How can I edit this file now? 
I am completely new to ubuntu and don't understand much in command line or terminal operation. Please help. 

Thanks

---

### Post by ajgreeny on 2015-07-04
Sorry, but I know nothing about fingerprint scanners and therefore need you to tell me a lot more about what you have done and what the file is that you now need to edit.

Without that information it is impossible for us to help you, so tell us the full pathway to the file in question, what the wrong changes are that you made, and where you found the information in the first place which informed you to make those changes.

---

### Post by shailesh_paranjpe2 on 2015-07-05
Well, I could figure it out. Basically, I logged into Ubuntu using USB Drive and used Sudo command to edit the common-auth file. That way, while using sudo, the system did not ask me for a password and I could undo all the changes I had done to the file and restore the original one. The system is now up and login is accepted. 
Thank you for your support any way. You can close this thread now.

---

### Post by ajgreeny on 2015-07-05
I am.glad you got this sorted.
I have marked the thread as solved on your behalf.

---

