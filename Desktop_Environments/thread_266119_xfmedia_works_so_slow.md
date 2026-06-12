---
title: "xfmedia works so slow"
date: 2006-09-26
forum: Desktop Environments
---

### Post by mozkaynak on 2006-09-26
I have xubuntu on my old machine (Dell OptipLex GXa). I think it has PIII on it.
I use xfmedia to play my music CDs but I am completely unsatisfied with it.
It opens my CD so slow and freezes so often. Does anybody have any idea about how to improve its performance?
I dont expect it work perfect but I used Windows 2000 and Fedora Core 4 with the same HW without any problem.

---

### Post by pseudonym on 2006-09-27
Have you got all the right codecs installed? If not, first make sure you have the extra software suppositories enabled by going [here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") and following the instructions if you haven't already.

Then run 'sudo apt-get install libxine-extracodecs w32codecs'. You will also need to edit the ~/.xine/config file to point xfmedia to the right place where the codecs are installed. Instructions on doing that are [here]("http://nongeeksight.blogspot.com/2006/07/multimedia-in-xubuntu-made-easy.html")

Once all this is done you should have much better performance with xfmedia. I used it once on hardware similar to what you're describing and it worked fine.

---

