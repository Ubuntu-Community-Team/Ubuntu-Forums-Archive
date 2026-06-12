---
title: "Lucid livecd creation -problem"
date: 2010-05-31
forum: Desktop Environments
---

### Post by venkivoice on 2010-05-31
Hi All,

I have tried to customize Lucid, everything went well untill iso creation. the total size of my custom directory is 1.5G but when creating iso the size of the iso is 1.1G, I dont know why it didnot reduce.

I have follwed this link [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Please find the message which I got during iso creation.

> [I]I: -input-charset not specified, using utf-8 (detected in locale settings)
Using GSTREAMER0_10_PLUGINS_BASE000.D;1 for  ./pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base_0.10.28-1_i386.deb (gstreamer0.10-plugins-base-apps_0.10.28-1_i386.deb)
Using LIBLAUNCHPAD_INTEGRATION1_000.D;1 for  ./pool/main/l/launchpad-integration/liblaunchpad-integration1.0-cil_0.1.35_i386.deb (liblaunchpad-integration1_0.1.35_i386.deb)
Using CRYPTO_MODULES_2_6_32_21_G000.U;1 for  ./pool/main/l/linux/crypto-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (crypto-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using MD_MODULES_2_6_32_21_GENER000.U;1 for  ./pool/main/l/linux/md-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (md-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using FIREWIRE_CORE_MODULES_2_6_000.U;1 for  ./pool/main/l/linux/firewire-core-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (firewire-core-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using NIC_PCMCIA_MODULES_2_6_32_000.U;1 for  ./pool/main/l/linux/nic-pcmcia-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (nic-pcmcia-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using MOUSE_MODULES_2_6_32_21_GE000.U;1 for  ./pool/main/l/linux/mouse-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (mouse-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using NIC_MODULES_2_6_32_21_GENE000.U;1 for  ./pool/main/l/linux/nic-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (nic-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using PARPORT_MODULES_2_6_32_21_000.U;1 for  ./pool/main/l/linux/parport-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (parport-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using PPP_MODULES_2_6_32_21_GENE000.U;1 for  ./pool/main/l/linux/ppp-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (ppp-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using PLIP_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/plip-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (plip-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using SCSI_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/scsi-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (scsi-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using NIC_SHARED_MODULES_2_6_32_000.U;1 for  ./pool/main/l/linux/nic-shared-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (nic-shared-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using FS_CORE_MODULES_2_6_32_21_000.U;1 for  ./pool/main/l/linux/fs-core-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (fs-core-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using VLAN_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/vlan-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (vlan-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using NFS_MODULES_2_6_32_21_GENE000.U;1 for  ./pool/main/l/linux/nfs-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (nfs-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using MESSAGE_MODULES_2_6_32_21_000.U;1 for  ./pool/main/l/linux/message-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (message-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using BLOCK_MODULES_2_6_32_21_GE000.U;1 for  ./pool/main/l/linux/block-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (block-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using SATA_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/sata-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (sata-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using SQUASHFS_MODULES_2_6_32_21000.U;1 for  ./pool/main/l/linux/squashfs-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (squashfs-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using FS_SECONDARY_MODULES_2_6_3000.U;1 for  ./pool/main/l/linux/fs-secondary-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (fs-secondary-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using CHAR_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/char-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb (char-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb)
Using VIRTIO_MODULES_2_6_32_21_G000.U;1 for  ./pool/main/l/linux/virtio-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (virtio-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using PATA_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/pata-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (pata-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using IRDA_MODULES_2_6_32_21_GEN000.U;1 for  ./pool/main/l/linux/irda-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (irda-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using NIC_USB_MODULES_2_6_32_21_000.U;1 for  ./pool/main/l/linux/nic-usb-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (nic-usb-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb)
Using PCMCIA_STORAGE_MODULES_2_6000.;1 for  ./pool/main/l/linux/pcmcia-storage-modules-2.6.32-21-generic-di_2.6.32-21.32_i386.udeb (pcmcia-storage-modules-2.6.32-21-generic-pae-di_2.6.32-21.32_i386.udeb) "[/I]I dont know whats wrong

Any help would be much appreciated.

Venkat

---

### Post by lazyb0y on 2012-03-04
Hi!

Same problem here - did you ever find a solution to this?!

---

### Post by lazyb0y on 2012-03-04
got it, I needed to add "-iso-level 4" as option!

---

