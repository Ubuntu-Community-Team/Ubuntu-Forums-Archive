---
title: "Problem with World of Padman installation"
date: 2007-12-07
forum: Gaming &amp; Leisure
---

### Post by Siva Chandran P on 2007-12-07
Hi,
 I downloaded the World of Padman(worldofpadman.run) from their site  and ran it(added executable permission) but it shows the installation dialogs without any text. First it shows the License Agreement with no text in text control and button, then it shows the Options dialog. There also no text in any of the controls and am not able to enter any text in the edit controls. It doesn't throw any error in console. 
```
./worldofpadman.run 
Verifying archive integrity... All good.
Uncompressing World of Padman 1.1-final..........................................................................................................................................................................
```
I am running Gutsy with Intel AGP. I have also attached the screenshots. Did anyone face this problem?

---

### Post by Siva Chandran P on 2007-12-09
The problem is internationalization. There is no setup.mo(gettext) for my locale(en_IN). So I changed my locale temporarily(export LANG=enUS) and installed World of Padman. I also faced the same problem in another game installation(I think its Tremulous). I am happy that finally I found the cause and solution for it.

---

