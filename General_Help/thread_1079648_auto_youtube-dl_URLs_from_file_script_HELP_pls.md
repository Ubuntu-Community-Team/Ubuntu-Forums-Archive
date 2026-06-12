---
title: "auto youtube-dl URLs from file script HELP pls"
date: 2009-02-24
forum: General Help
---

### Post by brdlvelixir on 2009-02-24
hi all. ok I'm using youtube-dl to download youtube videos to my comp, and I'm using a file called tube.sh to automate the process for a list of urls. so right now, tube.sh looks like this:
------------------------------------------------
youtube-dl -t -b [http://www.youtube.com/watch?v=video01](http://www.youtube.com/watch?v=video01)
youtube-dl -t -b [http://www.youtube.com/watch?v=video02](http://www.youtube.com/watch?v=video02)
youtube-dl -t -b [http://www.youtube.com/watch?v=blahblahblah3](http://www.youtube.com/watch?v=blahblahblah3)
youtube-dl -t -b [http://www.youtube.com/watch?v=blahblahblah4](http://www.youtube.com/watch?v=blahblahblah4)
etc....
------------------------------------------------

this works fine but it gets old having to open the file, delete old urls and replace with new urls all the time.

With linux everything is possible, so I'm wondering how I can simply open terminal and issue a command to delete the old contents of tube.sh and paste/append new urls to the file, then run a foreach loop executing "youtube-dl -t -b" for each url, or simply insert "youtube-dl -t -b " at the beginning of each line so each vid is downloaded in order when i run tube.sh

i know nothing about scripting. i was thinking something like:

echo [http://www.youtube.com/watch?v=video01](http://www.youtube.com/watch?v=video01) >> ~/tube.sh && echo [http://www.youtube.com/watch?v=video02](http://www.youtube.com/watch?v=video02) >> ~/tube.sh && echo etc...........

that appends the urls to the file but i still need to know how to auto delete those entries from the file when i want to download new vids the next time, and about the youtube-dl foreach loop, if that is even what's needed.

Thanks, any help is greatly appreciated.

---

### Post by prinny42 on 2009-02-24
I don't know much about scripting myself, and this would be a bit of a work-around, but perhaps you don't need to delete the entries each time.  Instead, you could simply have a separate file called "tube-template" or something that's exactly the same as the script itself except without all the URLs.  Then you could simply have it overwrite tube.sh whenever you want to remove the old URLs from it.

---

