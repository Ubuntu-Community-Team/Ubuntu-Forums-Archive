---
title: "wubi install and unistall does not work"
date: 2009-02-07
forum: General Help
---

### Post by swilkeni on 2009-02-07
Let me start in saying that Im a complete noob to Ubuntu and wanted to try it out through Wubi

I have just tried to install wubi 8.10 on Vista 64 bit with 15GB storage.  During the installation my progress bar stopped for about 30 min and I canceled the installation and tried to reinstall.  The reinstall seemed to work at first but then I rebooted and was given no choice to boot to ubuntu, my computer just booted direct to windows.  

When I tried to uninstall wubi, the uninstaller said it completed, but did not do anything and did not give my 15GB back.  I have searched these formus a bit and found instructions on a manual install.  Those instruction say to delete C:\ubuntu and C:\wubildr* folders.  I have no C:\wubildr* and when I delete the ubuntu folder, I dont gain the 15GB back.  I have not proceeded with any of the other manual install instruction.

I have also tried to download a new uninstall file from the WubiGuide pages, and that did not work.

Here is the wubi log from my temp folder, file: Wubi-8.10-rev515.  There is also a Wubi-8.04.1-rev506 file and can post the contents if needed.

============ Installer ============
PLUGINSDIR=C:\Users\Steve\AppData\Local\Temp\nsx483D.tmp
detect_all
Parsing cmdline "C:\Users\Steve\AppData\Local\Temp\7zS403F.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-259 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
isInstallationDrive D:\ubuntu
AlreadyInstalled=false OldInstallationDrive= InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1720; Volume name ; Max #/chars in vol name 7170632; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name HP_RECOVERY; Max #/chars in vol name 7170636; Volume Serial # -367855417; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6296232; Volume name ; Max #/chars in vol name 45; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 220344
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=Steve-PC
ComputerName=STEVE-PC
EnvUsername=Steve
UserDomain=Steve-PC
UserInfoName=Steve
UserProfileFolder=C:\Users\Steve
UserProfileName=Steve 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 6608224; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name HP_RECOVERY; Max #/chars in vol name 6608228; Volume Serial # -367855417; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Skipping drive D:, not enough free space 1882 <= 5000
Drive list = C:
ChangeInstallationDrive to c:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=3b9575338d15124f6d6346f1631af332
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = File check failed
CheckCD status = failure
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/30/08 08:47:06 Eastern Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 4afe56cd0ab998e6a2bbe45b63344c81
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink md5=4afe56cd0ab998e6a2bbe45b63344c81
Download status=cancel
User cancelled download, quitting.
============ Installer ============
PLUGINSDIR=C:\Users\Steve\AppData\Local\Temp\nsj633D.tmp
detect_all
Parsing cmdline "C:\Users\Steve\AppData\Local\Temp\7zS5FB2.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-259 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=false
IsValidFileSystem C:
Drive & Path name 1720; Volume name ; Max #/chars in vol name 6774424; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name HP_RECOVERY; Max #/chars in vol name 6774428; Volume Serial # -367855417; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6496784; Volume name ; Max #/chars in vol name 44; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 219682
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=Steve-PC
ComputerName=STEVE-PC
EnvUsername=Steve
UserDomain=Steve-PC
UserInfoName=Steve
UserProfileFolder=C:\Users\Steve
UserProfileName=Steve 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 6616528; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name HP_RECOVERY; Max #/chars in vol name 6616532; Volume Serial # -367855417; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Skipping drive D:, not enough free space 1882 <= 5000
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=3b9575338d15124f6d6346f1631af332
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = File check failed
CheckCD status = failure
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/30/08 08:47:06 Eastern Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 4afe56cd0ab998e6a2bbe45b63344c81
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink md5=4afe56cd0ab998e6a2bbe45b63344c81
Download status=success:C:\ubuntu\install\ubuntu-8.10-desktop-amd64.iso
ISO file ubuntu-8.10-desktop-amd64.iso retrieved!!!
CopyKernel isokernel=casper\vmlinuz, iso=C:\ubuntu\install\ubuntu-8.10-desktop-amd64.iso, cddrive=E:
Extracting with 7z kernel/initrd from C:\ubuntu\install\ubuntu-8.10-desktop-amd64.iso
UncompressFilesPriorInstall
Drive & Path name C:\ubuntu\install\ubuntu-8.10-desktop-amd64.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
DoMenuLst C:\ubuntu\install\boot\grub\menu.lst
editBootDrive
editBootDrive NT
CopyWubildr
CopyWubildrMbr
EditBootIni
Drive & Path name C:\ubuntu\install\ubuntu-8.10-desktop-amd64.iso; Volume name ; Max #/chars in vol name ; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive C: has filesystem NTFS
rootSize=14000 homesize=0, swapsize=1000, usrsize=0
AllocFile filename=C:\ubuntu\disks\root.disk size=14000
AllocFile status=success
AllocFile filename=C:\ubuntu\disks\home.disk size=0
AllocFile filename=C:\ubuntu\disks\swap.disk size=1000
AllocFile status=success
UncompressFilesAfterInstall
EjectCD
Ejecting CDHandle=536 for drive=E:
EjectCD DeviceIoControl exited with code 1 (1==success)
Installation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\Steve\AppData\Local\Temp\nsl903F.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
Uninstallation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\Steve\AppData\Local\Temp\nswE264.tmp
un.install
un.BackupIso
Backup \ubuntu\install\ubuntu-8.10-desktop-amd64.iso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
Uninstallation completed successfully!
============ Uninstaller ============
PLUGINSDIR=C:\Users\Steve\AppData\Local\Temp\nsr2AB9.tmp
un.install
un.BackupIso
un.CleanBcd
un.RemoveInstallationFolder \ubuntu
un.CleanThisDrive C:\
un.CleanThisDrive D:\
un.CleanRegistry Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
Uninstallation completed successfully!
============ Installer ============
PLUGINSDIR=C:\Users\Steve\AppData\Local\Temp\nsjB2BD.tmp
detect_all
Parsing cmdline "C:\Users\Steve\AppData\Local\Temp\7zSAB0D.tmp\wubi.exe" 
debug=, 32bit=, cdboot=
User account type=Admin
Memory=-259 MB
arch=amd64
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro= cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Changing icon to Ubuntu.ico
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
Found InstallationDrive C:\ubuntu
AlreadyInstalled=true OldInstallationDrive=C: InstallCompleted=true
IsValidFileSystem C:
Drive & Path name 1720; Volume name ; Max #/chars in vol name 6595816; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
IsValidFileSystem D:
Drive & Path name 1720; Volume name HP_RECOVERY; Max #/chars in vol name 6595820; Volume Serial # -367855417; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
IsValidFileSystem c:
Drive & Path name 6300104; Volume name ; Max #/chars in vol name 33; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size 2147352576
Drive c: has valid filesystem NTFS
Installation drive chosen = c:
FreeSpace in c: is 205964
DetectBackupFolder
IsBackupFolder C:\
IsBackupFolder D:\
GMT=-5
Country=US
Locale=en_US.UTF-8
TimeZone=America/New_York
Domain=localdomain
HostName=Steve-PC
ComputerName=STEVE-PC
EnvUsername=Steve
UserDomain=Steve-PC
UserInfoName=Steve
UserProfileFolder=C:\Users\Steve
UserProfileName=Steve 
detect_all finished
ShowMainPage
Making drive list
IsValidFileSystem C:
Drive & Path name 1786; Volume name ; Max #/chars in vol name 6562688; Volume Serial # 782974927; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive C: has valid filesystem NTFS
Adding drive C:
IsValidFileSystem D:
Drive & Path name 1786; Volume name HP_RECOVERY; Max #/chars in vol name 6562692; Volume Serial # -367855417; Max #/chars in dir/file names 255; File System Flags 2556159; File System Type NTFS; File System Name Size HDD
Drive D: has valid filesystem NTFS
Skipping drive D:, not enough free space 1882 <= 5000
Drive list = C:
ChangeInstallationDrive to C:
ChangeInstallationSize to 15
PopulateDistroList
DistroList = Ubuntu
PopulateLanguageListBox
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Changing artwork to distro=Ubuntu
Changing icon to Ubuntu.ico
InitMainPageToolTips
LeaveMainPage
ChangeInstallationSize to 4
LeaveMainPage
Locale=en_US.UTF-8
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
CreateInstallationFolders
MakeUninstall
Created C:\ubuntu\Uninstall-Ubuntu.exe
Created reg key HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
CopyDistFolders
GetIso
DetectCD
      Is Valid CD C:
CDInfo cleared
      Is Valid CD E:
      IsValid Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
      cdversion=8.10 cddistro=Ubuntu cdarch=amd64 cdcodename=Intrepid Ibex cdsubversion=Release cdbuild=20081029.2 
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Found a good ISO: Ubuntu 8.10 "Intrepid Ibex" - Release amd64 (20081029.2)
Found CD E:
Found CD cddrive=E:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
md5=3b9575338d15124f6d6346f1631af332
Checking md5 of E:\casper\filesystem.squashfs
CheckCD raw status = File check failed
CheckCD status = failure
      GetDistroInfo distrofullname=Ubuntu-amd64 distro=Ubuntu cddistro=Ubuntu cdarch=amd64 arch=amd64
      ->metalinkURL=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink
      ->isoKernel=casper\vmlinuz
      ->distroVersion=8.10
Checking/Downloading Ubuntu-8.10
retrieve_partial_files
check_internet_connection
Dialer online
connected
Trying remote metalink: [http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink)
get_md5 [http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink)
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink.gpg md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink.gpg
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/MD5SUMS-metalink md5=
Download status=success:C:\ubuntu\install\MD5SUMS-metalink
      Verifying signature C:\ubuntu\install\MD5SUMS-metalink.asc
0; gpgv: error loading `iconv.dll': The specified module could not be found.


gpgv: Signature made 10/30/08 08:47:06 Eastern Daylight Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Found md5 4afe56cd0ab998e6a2bbe45b63344c81
Downloading: trymefirst= url=http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-amd64.metalink md5=4afe56cd0ab998e6a2bbe45b63344c81
Download status=cancel
User cancelled download, quitting.


Thanks in advance for any help on this problem

---

