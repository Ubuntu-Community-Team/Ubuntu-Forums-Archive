---
title: "gFTP"
date: 2006-07-11
forum: Desktop Environments
---

### Post by fatallyhuman on 2006-07-11
I would like to use gFTP for uploading content to the web page I maintain. However, when I connect, I can see only one file "setup.rar" and that's it. None of my folders or other files. I can see them in windows programs, so I don't understand why gFTP doesn't see them. I run a web site for a summer camp, and I really don't want to be stuck using windows all summer. So if anyone has any ideas why this is happening, please let me know. Thanks.

---

### Post by fatallyhuman on 2006-07-11
Also, if you need more information about anything, just let me know and I'll try to get that to you. Also, it is a windows server that hosts the site. I don't know if that makes any difference or not, but I thought I'd throw it out there. Thanks

---

### Post by amunimanghi on 2006-07-11
I installed gftp. This is what I did. 

1. Under Host i put the url. Mine would look like this "example.netfirms.com"

2. I left port blank because I don't  have that number.

3. Under user I put my username.

4. Under pass I put my password.

5. Instead of http, I selected FTP.

It works just fine. Is your something like this. I would suggest to try it with the terminal.

Open the terminal up. Type ```
ftp
``` Then enter the URL. It will then ask for your username and password. After that, type in ```
 ls
``` See if all of your files are there. Other commands are like ```
put        to add a file. Example is put /home/ameen/test.htm test.htm.  it reads like this put [directory] [name of file you choose]

delete    that removes a file. Exampe is rm test.htm.
``` Try those out. Hope this helps.

---

### Post by fatallyhuman on 2006-07-11
I tried another FTP program in windows, and it did the same thing, so I know it wasn't gFTP's problem. I actually ended up emailing my web host, and it turned out that I didn't have the proper remote host listed when I tried to log in, so I could log in but not to the proper place. Everything is working now. Thanks for the help.

---

