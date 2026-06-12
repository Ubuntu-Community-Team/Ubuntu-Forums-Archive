---
title: "help with file"
date: 2008-12-06
forum: General Help
---

### Post by jesse c on 2008-12-06
I just downloaded a driver file from nvidia and its on my desktop but i dont know how to run it.A right click brings up a window that gives me options to 'run' or to 'run in terminal'.If i click 'run' the window goes away and nothing happens and the 'run in terminal' brings up an error screen that tells me i must run as root.Just for the record i have two books "Ubuntu For Non Geeks' and also the 'Linux For Dummies-Ubuntu'and there both over my head so step by step tutoring would be helpful

---

### Post by howefield on 2008-12-06
What is the name of the file you are trying to run ?

To run a command as root, preface it with sudo

---

### Post by cmay on 2008-12-06
> **jesse c said:**
> I just downloaded a driver file from nvidia and its on my desktop but i dont know how to run it.A right click brings up a window that gives me options to 'run' or to 'run in terminal'.If i click 'run' the window goes away and nothing happens and the 'run in terminal' brings up an error screen that tells me i must run as root.Just for the record i have two books "Ubuntu For Non Geeks' and also the 'Linux For Dummies-Ubuntu'and there both over my head so step by step tutoring would be helpful

first of all there should be no need to go fetch a driver from this site as in ubuntu there is a restricted driver manager.  second you mention nothing about what sort of file this is. so i can not say how to do with it. is it packed in some tar.gz archive or packed as a deb file.?  i can not say exactly from this information if it is a shellscript or what it is. 

i assume it is the drivers for a video card you need to install but i guess there should be an option to download this via the rrestricted driver managers in the system -> admintration -> drivers menu. 


i may suggest that you do not start to fetch stuff around the internet at more or less random like you have to do on windows but instead use the package management system that is in ubuntu as its more safe and reliable . 

in case it is a shell script and you have unpacked and put it you home folder then you have to open the terminal and type sudo ./name_of_file  to run it. which is why i recommend using the package manager or restricted driver manager instead since it is more safe and less trouble. also you do not need the terminal for doing this.

---

