---
title: "how to play .bin file?"
date: 2009-02-03
forum: General Help
---

### Post by abhilashm86 on 2009-02-03
my friend gave me a .bin file which has an video,so when i tried to play,it din't play, how to play .bin file video?

---

### Post by binbash on 2009-02-03
If you are sure that is a video file, that means it is a cd image.Convert it to iso with bin2iso .Then mount it with : 

mkdir /mnt/iso (you may need sudo)
sudo mount -o loop aasdasd.iso /mnt/iso

then go to /mnt/iso and open the video file

---

### Post by redilyn on 2009-02-03
Try the following, it might help

```

gmplayer <filename>.bin

```

---

### Post by kbutcher5 on 2009-02-03
He could ofcourse also just open it with vlc, but that is just my two cents?

---

