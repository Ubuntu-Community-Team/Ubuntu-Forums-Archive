---
title: "Gnumeric argues with me"
date: 2010-12-22
forum: Desktop Environments
---

### Post by The Cog on 2010-12-22
Whenever I edit a spreadsheet in Gnumeric, I have to have an argument about saving the edited version. First, it says it wants to save it in Gnumeric's XML format instead of whatever format I opened it in, and then I get a dialog warning me the file already exists, is it OK to overwrite it? 

All my spreadsheets are either .odt or .csv. I just want to be able to open, edit and save without an argument every time. It's like telling a child that it's bed time and having the same argument every night, and it's getting on my nerves.

Is there a setting where I can get gnumeric to obediently save the edited version, or do I just have to put up with the slower opening times of LibreOffice instead?

---

### Post by jbrefort on 2010-12-22
If you save as .csv, you'll loose all formating,formulas, and more. It makes sense to consider that saving as .csv is not safe.

About .ods, I don't see that, which gnumeric version are you using?

---

### Post by The Cog on 2010-12-22
I'm using Gnumeric 1.10.8 - the version that comes with Xubuntu 10.10. 

The .csv spreadsheets are in .csv format because they need to be in .csv format. After editing, they are uploaded to other systems that expect to be given CSV data. There is no point arguing with me about that format. I'm tired of arguing about it with Gnumeric already.

.ods is the ISO/IEC 26300 standard spreadsheet format. Gnumeric calls it ODF OpenOffice format.

I just want Gnumeric to save spreadsheets in whatever format they were in when I opened them. Without arguments.

---

### Post by jbrefort on 2010-12-23
I understand your point. But the cvs issue is not a bug, just a feature. Gnumeric imports and exports cvs, but we do not consider it as a speadsheet format.

ods files are saved correctly since 1.10.11, so you'll have to wait until it is updated in ubuntu. ODF export was judged mature only at this point.

---

### Post by The Cog on 2010-12-23
Ah. I understand. Thanks for the info.

---

### Post by cholericfun on 2011-11-28
I know this thread is old but on-the-fly, i didn't find any useful information about this exact behavior. Also i can't say i understand.
Given a file of supported filetype and requesting a Save, why is it that gnumeric is defaulting to the Save-As menu?

Also after having to manually make sure its saved as *.csv, closing the file is again riddled with warnings.

It's fine that gnumeric is importing a *.csv file into some other fileformat of its own preferences, but why does the user have to deal with the simple act of writing the modifications to the original file?

Never mind the confusingly rich variants of *.csv format (comma-seperated, colon-seperated, fixed widht...etc) which are not even mentioned while saving the file (all 3 issues appear in my case on a daily basis). 

Anyone has any insight on this "feature"?

---

