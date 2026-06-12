---
title: "Adding Virtual Users in Pure-Ftpd"
date: 2009-03-10
forum: General Help
---

### Post by Mal3ko on 2009-03-10
How do I add ftp users that have their home folder point to a folder in real user account?

eg, I created a user account that has ssh access, which has home folder at /home/schools/

and now i want to add a virtual ftp user which will have home folders in /home/schools/assigns/

files uploaded by that user will be assigned will files/folder permissions own by user acc 'schools'

---

### Post by sonicb00m on 2009-03-10
I think one of the solutions is to use mysql and create a login user name and path. It's a bit fiddly to do what you want otherwise. The ftp will currently login to the same location as the user you created.

There are various guides on virtual accounts on howtoforge.com

---

### Post by Mal3ko on 2009-03-10
Yea. I got it to work finally. Thanks to some folks on #ubuntu for some hints

I just need to create a user with specifying the real user account in both - u & -g and set the home dir of the ftp account to that folder

sudo pure-pw useradd student -u school -g school -d /home/school/assigns/

---

### Post by sonicb00m on 2009-03-10
aha i see i thought you wanted to have a seperate location for the SSH login from the ftp. I presume setting that path like that makes the SSH default to the "assigns" directory?

---

