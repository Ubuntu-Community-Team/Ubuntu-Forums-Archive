---
title: "Reimaged bootsplash conflict"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by mr4thjuly on 2007-07-19
Ok so here is my problem. I have a custom made image of ubuntu. In that custom image (which I use to re-image whenever I have a problem with ubuntu) I have a custom bootsplash image. I wrote a script that will install my bootsplash in parallel with the default bootsplash of ubuntu. Everything runs fine except that every time I must run apt-get update and apt-get dist-upgrade 2 times. This is a very annoying problem. How can I modify my script so that this problem is solved. Here is a copy of my script. I think my problem will be solved if I do not install my bootsplash image in parallel, but I am unable to find a way out.
Thanks in advance to anyone who replies.

#!/bin/sh

set -e

if [ "$1" = "configure" ]; then
   # Generate the final .so file for usplash
   DIR_SO_ALT_ABS="/usr/lib/usplash"
   IMG_SO_ALT="usplash-artwork.so"
   IMG_SO_ALT_ABS=${DIR_SO_ALT_ABS}/${IMG_SO_ALT}
   DIR_SO_DEST_ABS="/usr/local/lib/usplash"
   IMG_SO="mpower-usplash.so"
   IMG_SO_DEST_ABS=${DIR_SO_DEST_ABS}/${IMG_SO}

   # Use the Debian alternatives system to install our bootsplash image in
   # parallel to the default bootsplash image
   update-alternatives --install ${IMG_SO_ALT_ABS} ${IMG_SO_ALT} ${IMG_SO_DEST_ABS} 55
   update-alternatives --set ${IMG_SO_ALT} ${IMG_SO_DEST_ABS}
   update-initramfs -u
   dpkg-reconfigure linux-image-$(uname -r)

   # Modify GRUB configuration so usplash will work
   GRUB_CONF="/boot/grub/menu.lst"
   TMP_FILENAME="/tmp/new-menu.lst"

   echo "Modifying GRUB configuration to support our splash image..."

   old_menu=$(cat ${GRUB_CONF})
   new_menu=$(echo "${old_menu}" | sed '/^kernel.*vmlinu\|zImage.*/s/[ ]*vga=[0-9]*//')

---

