---
title: "Ventrilo sound quit after update to 0.9.26, how to revert"
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by aswells on 2006-11-28
I had ventrilo running in wine so that I could hear everyone talking (only one person at a time though) and I could activate my hotkey, even though ubuntu doesnt currently support my integrated sound so my mic didnt work. After I updated to 0.9.26, when I start ventrilo I cannot hear any sounds and get the following messages in the terminal:

```
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17

```
They look like registry entries to me, but I am not sure.

Also, is there a way for me to revert back to 0.9.25? I was thinking I could move my drive_c folder, uninstall wine and reinstall the correct version then put the folder back in the right place, are there any forseeable problems with that?

Thanks

*EDIT*  I got sound back by enabling ALSA and OSS audio, but since this is advised against by wine I would like to solve this problem using only OSS. Any explanation on the error messages would be helpful.

---

### Post by aswells on 2006-11-28
Ok, changing all of the wine dll files with the windows native dll versions does not make every program work perfectly, its just very time consuming.

*EDIT* Ok, got everything working again, disreguard this post

---

