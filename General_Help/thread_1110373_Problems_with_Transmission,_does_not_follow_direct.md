---
title: "Problems with Transmission, does not follow directions"
date: 2009-03-29
forum: General Help
---

### Post by dch528 on 2009-03-29
Whenever I open a torrent with multiple files in Transmission, I usually only select a few of these files so I can save disk space, or to stop the download of unneeded data. Although I tell Transmission not to download certain files when a torrent is added, it still downloads half of them! How can I stop this? What other Bittorrent clients are there that actually work?

---

### Post by cariboo on 2009-03-29
I would suggest using Deluge, it is in the repositories. I have used it for downloading partial torrents and it works quite well.

Jim

---

### Post by lovinglinux on 2009-03-29
I also suggest Deluge. It has an option to download only selected files from torrents with multiple files. But then you need to use "Full allocation" option, which means it will reserve all the space to download the selected file in advance. Sometimes it will also allocate the space necessary to download one file before or after the one you want, because they can share some pieces of the torrent data. This is due to the way torrents of multiple files are created, by dividing the whole amount of data into tiny packets of identical size.

---

### Post by chrx on 2009-03-30
i thought so too. but when checked the files they were all empty.
every client does this, even deluge...

---

### Post by hyper_ch on 2009-03-30
or use rtorrent

---

### Post by robobot on 2009-03-30
The problem is that torrents are divided into pieces (usually 128 kB to 4MB in size). When you tell the torrent client to download a certain file, it downloads all the pieces which contain parts of that file, not the individual file. Sometimes the pieces contain the end of one file and the beginning of another, which will cause parts of both files to be downloaded. Also, if you have very small files such as pictures or text, each piece may contain several files.

For example, say you have a torrent containing a 700 MB movie, a 3 kB info text file, and a 96 kB screenshot image. If the torrent is split into 1 MB pieces, the first piece will contain the image, the text, and part of the movie. If you specify to download only the movie, the first piece will be downloaded since it contains part of the movie. The two files you don't want will still be downloaded, since they are stored in a piece which contains part of the movie.

You can always delete the files you don't want after you finish downloading and seeding.

---

