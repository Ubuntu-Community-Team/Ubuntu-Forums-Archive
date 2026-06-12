---
title: "Authoring/burning DVD"
date: 2005-10-20
forum: Desktop Environments
---

### Post by ColinG on 2005-10-20
Has anybody manages to author and burn a dvd in Kubuntu 5.10. There is no equivalent package to dvdstyler in the supported repositorires and qdvdauthor won't work - it just does not produce any output.

I can edit the Video and create the mpeg in Kino but that;s not much use if I can't burn it to dvd.

There was/is a similar problem on mandriva 2006 where dvdstyler won't work  and it seems that there was/is an issue with the latest release of MJPEGTOOLS which dvdstyler uses

Help would be appreciated otherwise its back to Windows for video editing:(

---

### Post by reet on 2005-10-27
I have finally got DVDStyler working on Ubuntu 5.10. You are correct, mjpegtools is at fault.

All I did was downgrade mjpegtools and libmjpegtools0 to 1.6.2-09 and all is well.

Good luck.

---

### Post by ColinG on 2005-10-28
Thanks for that.

Uninstalling the new and replacing with the old - why did I not think of that:oops: . Where did you find the old debs - or is there a more automated way of doing this via Apt?

Once again, many thanks.

---

### Post by reet on 2005-10-28
I found them in the Marillat repositories. If you don't have them in your sources.list edit /etc/apt/sources.list and add this line to it:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

Then in Synaptic you click on mjpegtools and hit "force version" under the package menu. I'm sure you can figure it out from there, then do the same to libmjpegtools0.

For me, forcing the version involved removing transcode, but I don't use it anymore anyways so that was okay for me. If you need transcode, you will have to force the version to one in the the marillat repository as well.

---

