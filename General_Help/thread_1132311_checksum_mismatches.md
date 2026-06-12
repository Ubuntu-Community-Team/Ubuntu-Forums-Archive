---
title: "checksum mismatches"
date: 2009-04-21
forum: General Help
---

### Post by Robert Bertrand on 2009-04-21
can anyone tell me how to fix these,i did check them somewhat but dont know how to repair.1b8195fafe9b881b019a7d459dda86c6c054218f  /lib/modules/2.6.24-19-generic/modules.pcimap
519f3cd63c7ce4b7d29b628ea6d50aa6150d219a  /lib/modules/2.6.24-19-generic/modules.dep
a3a9a7475754195585b8e1c95b5fc2185dbbda37  /lib/modules/2.6.24-19-generic/modules.ieee1394map
40b478cd18c91a5437171431c69d786e3bcde499  /lib/modules/2.6.24-19-generic/modules.usbmap
e7fa988ec2cc87f8ae04a25e1a9a9e8c514cc97c  /lib/modules/2.6.24-19-generic/modules.isapnpmap
c0fd35abfc61eefc142b85157448f6352a70b815  /lib/modules/2.6.24-19-generic/modules.seriomap
8c9d78c8f8c0664b0b30f3006481d4e96ed315ed  /lib/modules/2.6.24-19-generic/modules.alias
543e9abf2cfccf418255b7905b159d93459f77c6  /lib/modules/2.6.24-19-generic/modules.symbols
5ce57ee4d4f22411cf24e282f1e039bcaf4353ea  /lib/modules/2.6.24-23-generic/modules.pcimap
50b739d75acac6a56494f90a306a7094fd63221a  /lib/modules/2.6.24-23-generic/modules.dep
a3a9a7475754195585b8e1c95b5fc2185dbbda37  /lib/modules/2.6.24-23-generic/modules.ieee1394map
87149ccc314f27de44eca5f847321b5648818c24  /lib/modules/2.6.24-23-generic/modules.usbmap
e7fa988ec2cc87f8ae04a25e1a9a9e8c514cc97c  /lib/modules/2.6.24-23-generic/modules.isapnpmap
457906d36f901bb1056d05430792a1b5be5f3a8e  /lib/modules/2.6.24-23-generic/modules.inputmap
c0fd35abfc61eefc142b85157448f6352a70b815  /lib/modules/2.6.24-23-generic/modules.seriomap
6289240ba7ec55eb2366427b709d3ce3b8299802  /lib/modules/2.6.24-23-generic/modules.alias
b2bd28064399634d95e2eaf9f6b9204c02d0088e  /lib/modules/2.6.24-23-generic/modules.symbols
60ee298fe7f0728d0305cd6e2b3741da77394265  /usr/lib/openoffice/share/config/javasettingsunopkginstall.xml

---

### Post by jsowoc on 2009-04-21
I don't know how you know that these files are corrupt, but you could reinstall the package that contains the file. All but the last one look like kernel modules, so reinstalling linux-modules (through Synaptic) would give you clean versions of those files.

The final file looks like OpenOffice, but you probably don't want to reinstall all of the OpenOffice packages. There was some command to find out exactly which package contains a given file... anyone?

edit/update: the program is called "apt-file". To find out which package includes a specific file, run:
sudo apt-get install apt-file
sudo apt-file update
apt-file find 'filename'

then to reinstall a specific package, I suggest
sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall 'packagename'

---

