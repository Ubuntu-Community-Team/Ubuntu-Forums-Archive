---
title: "ubuntu proftpd login issue"
date: 2009-02-11
forum: General Help
---

### Post by nvid1a on 2009-02-11
hello there,

i dont know if this post should be here in general but here it goes.

i have a computer in my office working with linux and i use it only as an ftp server with the proftpd, well it works very very well its just that i want to fix a little login issue and i dont know how to do it.

when you login to the computer via a ftp client it doesnt happen but when you login via the ftp that windows has ( lets say you are on the my computer windows and in the address bar you put [ftp://myserverip](ftp://myserverip) ), well when you do that windows logs in but it doesnt prompt for the user and the password it just shows a black screen with a file that call welcome.msg.

when you are there you click the right botton of the mouse and you have to click on the login as... to prompt for that screen.

so i believe that there is problem with the proftpd configuration that doesnt give the instruction to prompt for the login screen, but as i said it only happens with the windows own ftp client when you use a real ftp client with GUI o command-line it works perfectly.

i will appreciate your help, thank you very much.

greetings from chile.

---

### Post by Kain000 on 2009-02-11
Hello,

Humm I like to use proftp alot, as a helpful gui to set up my FTP server, I dont mind the command line but a gui makes alot of things easier.

So anyway, it may be a windows thing, I havnt had this happen before tho, 

perhaps somthing to do with what directory people access without a username?    

message .txt is your editable welcome message with all the info for that server you want to make available, ie; admin name and emsil for contact info, list of what the server is for ect.

I've never been able to access even that directory without logging in. 

my bet it somthing with your permissions/directories.

Check what directory your welcome message.txt is in and go from there.

hope this helps

---

