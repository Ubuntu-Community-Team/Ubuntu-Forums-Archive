---
title: "Ubuntu watching movies and playing music"
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by ubuntoexpert on 2008-03-15
When i want to play music with Ubuntu, it asks me to convert the .wav file to the format that ubuntu recogonizes.

This is because Linux can't have any proprietory program in it's bundle of softwares in order to sell it's OS as free.

1.How do i convert the .wav file to the format that Ubuntu recogonizes.
2.How do i convert movies into a format the Linux Ubuntu recogonizes.

---

### Post by HoCuS_PoKuS on 2008-03-15
Are you sure about that? I got a .wav file to play on my side. 1) A sound file in Rythmbox. 2) I got a small movie file to play in VLC along with a audio clip as well.

---

### Post by Zorael on 2008-03-15
If you're not very concerned about the libre type of free (free as in freedom, not free as in free beer), you could install the packages with the proprietary mp3/etc codecs.

See [this wiki entry](https://help.ubuntu.com/community/RestrictedFormats) for more information.

---

### Post by prshah on 2008-03-15
> **ubuntoexpert said:**
> When i want to play music with Ubuntu, it asks me to convert the .wav file to the format that ubuntu recogonizes.

This is because Linux can't have any proprietory program in it's bundle of softwares in order to sell it's OS as free.

1.How do i convert the .wav file to the format that Ubuntu recogonizes.
2.How do i convert movies into a format the Linux Ubuntu recogonizes.

You can install the restricted extras (which will allow you to play MP3, wav, video etc) with the command ```
sudo apt-get install ubuntu-restricted-extras
``` Make sure that it's not illegal in your country to actually use these.

For conversion of audio (wav) files you can use  ```
sudo apt-get install soundcoverter
```

For conversion of video files you can use   ```
sudo apt-get install avidemux
```. Note that video conversions usually take hours for large videos.

---

### Post by logos34 on 2008-03-15
You mean Ubuntu won't play .wavs out-of-the-box?  You have to install restricted formats stuff?  I didn't know that.

---

### Post by Zorael on 2008-03-15
Googling around a bit, it looks like you shouldn't need to.

---

