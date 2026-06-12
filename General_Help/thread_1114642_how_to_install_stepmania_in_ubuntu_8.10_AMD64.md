---
title: "how to install stepmania in ubuntu 8.10 AMD64"
date: 2009-04-03
forum: General Help
---

### Post by opensourcethis on 2009-04-03
i had a hell of a time trying to install stepmania in ubuntu 8.10 AMD64. so i made this tutorial after hours of frustration searching forums and downloading packages that didn't work, this is what i found out.  i hope it helps.




first go here:  [http://www.getdeb.net/release/2594](http://www.getdeb.net/release/2594)

download BOTH the stepmania4 and stepmania4-data  deb packages.

these will not install without resolving some dependency issues first.  synaptic package manager could not find the packages i needed.  so do it manually.  you'll need: 
libavformat1d
libavut1d
linavcodec1d

and here are the links to download deb packages for all of them

[http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.3_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu4.2_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu4.2_amd64.deb)

after downloading and installing these packages run the stepmania4-data package then the stepmania4.

then stepmania 4 should be added to your games folder.

if you have any questions feel free to ask.  i will try and help as best as i can.

---

### Post by Kjue on 2009-08-11
The two URLs are broken or misspelled for some reason, correct URLs are:

[http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.3_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.3_amd64.deb)

And you may also need to install dependency **libdc1394-13** using aptitude:

```
sudo aptitude install libdc1394-13
```

---

