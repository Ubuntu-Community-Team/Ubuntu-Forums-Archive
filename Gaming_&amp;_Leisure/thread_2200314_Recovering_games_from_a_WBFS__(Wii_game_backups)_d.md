---
title: "Recovering games from a WBFS  (Wii game backups) drive"
date: 2014-01-18
forum: Gaming &amp; Leisure
---

### Post by sienile on 2014-01-18
Recently, I tried to update my WBFS drive in Ubuntu 13.10. I found that no matter what software I installed, I could not mount the WBFS partition. It always showed up as "unknown partition" in any partition editor. But in my search to try to make the partition mountable, I found a way to recover my games so I could put them on a FAT32 partition (I found that WBFS partitions have become obsolete over the last few years in favor of WBFS image files).

The first step is to create an image of the WBFS partition. Go to Disks and find the partition. Click the button that looks like gears and select "Create Disk Image...". Save the image file in an empty folder (to prevent the backup manager from searching your entire hard drive later). This may take a VERY LONG TIME. I had a 990 GB partition and it took a little over 26 hours to make the image.

Step 2 is to convert the image into individual WBFS images. To do this you will need Wii Backup Fusion ([http://sourceforge.net/projects/wiibafu/](http://sourceforge.net/projects/wiibafu/)). It's available in source and deb format for linux. I used the deb 1.1 version.
Under the Files tab, select "Load" and pick the directory that you put your partition image in. Once it's loaded, hit "Select all / none" and then "Transfer to image". 
Select the directory to dump your images to and then pick the ".wbfs" image format and hit the OK button. After the status bar at the bottom stops showing a progress bar (it will show a bar for every game, let it do all of them) you images are ready.

**Required extra step for large files:** Any file larger than _exactly_ 4GB will need to be split. This is also done using the "Transfer to image" dialog. Just click the "Split" button before hitting OK. (Just to be sure I changed my value to "3.9GB" instead of the default "4GB".) After this you will have a .wbfs and a .wbf1 file. Both are required for the game to work.

Finally, format a disk to FAT32 and put the files in a directory named "WBFS" off the root of that disk. (_This is mandatory_. Loaders will not recognize any .wbfs files not in this directory!) Then it should work with your Wii backup loader. I personally use Configurable USB Loader and it works great.

**Note:** If you have NTFS support on your Wii, you can use that instead of FAT32 to avoid having to split large files... but you will lose GameCube backup support. That's why I didn't recommend it.

---

### Post by Jakub_Sadowski on 2014-07-11
I was running a 64-bit LiveCD session with insufficient memory to install ia32-libs (for 32-bit compatibility since WiiBaFu is only 32-bit with no source code available to recompile for ia64)...so I found another alternative which turned out to be awesome:  wiithon
[http://justplainobvious.blogspot.ca/2010/06/how-to-manage-wbfs-partitions-in-ubuntu.html](http://justplainobvious.blogspot.ca/2010/06/how-to-manage-wbfs-partitions-in-ubuntu.html)

If, like myself, you're looking for a 1-shot use and don't wanna muck around with your repos a link to one of the DEB files listed in the link below will quickly and conveniently install it:
[http://ppa.launchpad.net/wii.sceners.linux/wiithon/ubuntu/pool/main/w/wiithon](http://ppa.launchpad.net/wii.sceners.linux/wiithon/ubuntu/pool/main/w/wiithon)

That was supremely easy...how far Ubuntu has brought Linux in the last decade is nothing short of amazing.  I recall what a hassle this sort of thing used to be in Debian 15 years ago...

---

### Post by mynick2 on 2014-11-02
@sienile

Thank you for so much information about managing Wii games, I was searching information about using FAT32 partitions instead of this stupid WBFS. You gave me some pointers :).

---

