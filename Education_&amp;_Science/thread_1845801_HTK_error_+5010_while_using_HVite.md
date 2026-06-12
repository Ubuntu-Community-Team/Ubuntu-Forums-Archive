---
title: "HTK error +5010 while using HVite"
date: 2011-09-17
forum: Education &amp; Science
---

### Post by sotstas on 2011-09-17
Hey there people!

I have a problem while using the HTK (Hidden Markov Model Toolkit).
I'm using my own data for it (not voice) and made all conversions needed.
I'm past the Initialisation and Training of my models (with the simplest way possible), but my program really unreasonably won't get past the testing phase. The code I use is:
```

%Initialize HMMs
HInit -I katas.mlf -w 1.0 -S 'train/train_heianshodan.scp' -M hmms/hmm0 'proto/heianshodan'
HInit -I katas.mlf -w 1.0 -S 'train/train_heiannidan.scp' -M hmms/hmm0 'proto/heiannidan'
HInit -I katas.mlf -w 1.0 -S 'train/train_heiansandan.scp' -M hmms/hmm0 'proto/heiansandan'
HInit -I katas.mlf -w 1.0 -S 'train/train_heianyodan.scp' -M hmms/hmm0 'proto/heianyodan'
HInit -I katas.mlf -w 1.0 -S 'train/train_heiangodan.scp' -M hmms/hmm0 'proto/heiangodan'


%Re-estimate parameters of HMMs
HRest -I katas.mlf -w 1.0 -T 5 -S 'train/train_heianshodan.scp' -M hmms/hmm1 'hmms/hmm0/heianshodan'
HRest -I katas.mlf -w 1.0 -T 5 -S 'train/train_heiannidan.scp' -M hmms/hmm1 'hmms/hmm0/heiannidan'
HRest -I katas.mlf -w 1.0 -T 5 -S 'train/train_heiansandan.scp' -M hmms/hmm1 'hmms/hmm0/heiansandan'
HRest -I katas.mlf -w 1.0 -T 5 -S 'train/train_heianyodan.scp' -M hmms/hmm1 'hmms/hmm0/heianyodan'
HRest -I katas.mlf -w 1.0 -T 5 -S 'train/train_heiangodan.scp' -M hmms/hmm1 'hmms/hmm0/heiangodan'

%Create a network for our HMMs
HBuild HMM_list network

%Test the HMMs
HVite -H hmms/hmm1 -T 1 -i recout.mlf -l '*' -w network -S 'test/test_old.scp' dictionary HMM_list
HVite -H hmms/hmm1 -T 1 -i recout.mlf -l '*' -w network -S 'test/test_new.scp' dictionary HMM_list

%Export results
HResults -I katas.mlf HMM_list recout.mlf

```So the HVite gives me this error msg:
  ERROR [+5010]  InitSource: Cannot open source file heianyodan
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+3228]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HVite

Any ideas why? In the hmms/hmm1 file the heianyodan model exists and is readable. Even when I delete it from the list, the same error comes up for the rest of the models, so it's not about that specific one. Is there an error with the location reference?

Thank you so much for your help! I'm really stuck!:mad:
Sot

---

### Post by dabraude on 2011-10-27
This sort of error is normally caused by a mismatch in the hmmdefs file

---

