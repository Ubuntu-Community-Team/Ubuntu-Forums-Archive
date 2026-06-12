---
title: "Business app, time recording"
date: 2011-06-26
forum: Desktop Environments
---

### Post by essexboyracer on 2011-06-26
Hi All, does anyone know of an application that will record how long a user spent within predefined folders or within a file opened within that specified folder.

I work from home and am looking to find a way to record how long I spend on a client.

---

### Post by jerrrys on 2011-06-26
worklog...its in the software center

---

### Post by essexboyracer on 2011-06-27
thanks Jerry, nice program although a bit sparse on instructions (being a CLI only with no GUI, spent 5 minutes looking for it in Applications menu, hey ho)

1. Create a file with the following contents, save the file in your home dir (or a sub folder), call it what you like, I called it 'worklog'

```
# Worklog project file
# note that projects appear in Worklog in REVERSE order
# Format as follows:
# letter:Title
# Letter is a key that you press to start/stop a timer for the given project in title
m:Client One
c:Client 2
t:Making a tea
```

2. Create a launcher on the panel. Type is 'Application in terminal'. The command should be:

```
worklog /home/username/time/worklog
```

Or wherever you saved the text file created above

3. Once the program runs it is fairly self explanatory

4. It will create various log files on a per project basis, these are saved in the same directory that the worklog file lives in

---

