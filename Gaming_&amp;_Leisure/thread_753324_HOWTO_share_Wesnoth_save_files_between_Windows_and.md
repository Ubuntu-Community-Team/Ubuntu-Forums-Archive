---
title: "HOWTO: share Wesnoth save files between Windows and Linux"
date: 2008-04-12
forum: Gaming &amp; Leisure
---

### Post by maybeway36 on 2008-04-12
I used this technique to share my Battle for Wesnoth save files between Linux and Windows, and I thought it might be of use to other members of the communuty.

Prerequisites:
*Your Linux home directory must reside on an ext3 or ext2 partition
*Windows must be installed on an NTFS partition

1. Install Battle for Wesnoth on both Windows and Linux. Run and close it once in each OS.

2. On Windows, install the ext2 driver from [http://www.fs-driver.org/](http://www.fs-driver.org/)[http://www.fs-driver.org/]("http://www.fs-driver.org/"). Make sure your Linux partion corresponds to a Windows drive letter.

3. Also on Windows, install Junction Link Magic from [http://www.rekenwonder.com/linkmagic.htm]("http://www.rekenwonder.com/linkmagic.htm").

4. Run Junction Link Magic and click Create. In the left pane, navigate to C:\Program Files\Wesnoth [version number]\userdata\saves. In the right pane, go to [Linux drive letter]\home\[username]\.wesnoth\saves.

5. Click Create, and close Junction Link Magic.

6. The Wesnoth for Windows saves folder should now point to the Linux version's folder, and the two versions will be able to use each other's save files.

---

