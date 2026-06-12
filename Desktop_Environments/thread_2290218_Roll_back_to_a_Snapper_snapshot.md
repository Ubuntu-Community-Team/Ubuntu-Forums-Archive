---
title: "Roll back to a Snapper snapshot"
date: 2015-08-10
forum: Desktop Environments
---

### Post by Gijsbert_Wiesenekk on 2015-08-10
I recently switched to btrfs for my root filesystem so that I could use snapshots to roll back failed installations. I decided to use snapper to create the snapshots, and wanted to test if I could roll back to a snapshot if I could not longer boot from my root filesystem because of a failed installation. The instructions I Googled were sometimes outdated (so I messed up my root filesystem) or not complete (so I could no longer use snapper after a restore), so I am posting these tested instructions now for reference.
I installed ubuntu 14.04.3 on /dev/sda2 and selected btrfs during installation. This gives me two subvolumes called '@' and '@home' on /dev/sda2. I installed snapper and created a default snapshot configuration for /. I am assuming you can can longer boot from the root filesystem so you have to boot from a USB key.
Open a terminal, mount the partition containing the subvolumes and list the snapshots:
$ sudo mount /dev/sda2 /mnt
$ sudo btrfs subvolume list /mnt
.. path @home
.. path @
.. path @/.snapshots
.. path @/.snapshots/1/snapshot
.. path @/.snaphotss/2/snapshot
.. (many more snaphots)
Move the broken subvolume out of the way:
$ sudo mv /mnt/@ /mnt/@.broken
But this will also change the path to the snapshots:
$ sudo btrfs subvolume list /mnt
.. path @home
.. path @.broken
.. path @.broken/.snapshots
.. path @.broken/.snapshots/1/snapshot
.. path @.broken/.snaphotss/2/snapshot
.. (many more snapshots)
Recreate the @ subvolume by creating a snapshot of the snapshot you want to restore to (in this case 2):
$ sudo btrfs subvol snapshot /mnt/@.broken/.snapshots/2/snapshot /mnt/@
Check that the subvolume has been created:
$ sudo btrfs subvolume list /mnt
.. path @
.. (many more subvolumes)
You can delete any or all of the @.broken snaphots using:
$ btrfs subvolume delete path-to-subvolume
If you now reboot you will find that snapper will no longer be able to create snaphots. The root cause is that the 'directory' /.snaphots is no longer a subvolume, but you cannot delete it because you will get the error that the directory is not empty although an ls -a shows that it is. So before you reboot remove the .snapshots directory and re-create it as a subvolume:
$ sudo rm -rf /mnt/@/.snapshots
$ sudo btrfs subvolume create /mnt/@/.snapshots
and reboot.

Regards,
Gijsbert

---

### Post by grahammechanical on 2015-08-10
A couple of us on the Ubuntu Development Version section of this forum experiemented with BTRFS the other year. We even managed to roll back a Ubuntu version upgrade. Did you know that if we install apt-btrfs-snapshot we then get a recovery mode option of apt-snapshot [revert to old snapshot & reboot]?

I stopped using BTRFS because it lacks a GUI snapshot manager. I tried Snapper. I did not like it. I could not get it working. I ended up modifying the recovery mode scripts so that the recovery menu would load from the terminal and I could then delete old snapshots as I wanted.

Regards

---

