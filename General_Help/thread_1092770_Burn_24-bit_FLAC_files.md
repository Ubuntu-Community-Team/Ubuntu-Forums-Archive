---
title: "Burn 24-bit FLAC files"
date: 2009-03-10
forum: General Help
---

### Post by stealth17 on 2009-03-10
How do I burn 24/96 flac files to a regular audio CD? I know you have to convert it but I cannot seem to get the files to convert. I've been googling forever without results. Here is what I tried but I get an error file type `auto' not found....

```
# Decode to WAV files
flac -d *.flac

# Create destination folder
mkdir resampled

mv *.wav resampled
cd resampled

# Rename to remove all strange chars
rename 's/ /_/g' *.wav

# In this case we use find to execute sox for each file, Here you can edit the sox options!
find . -name "*.wav" -exec sh -c 'sox -S $0 -r 48000 $0.wav && cat $0.wav > $0 && rm $0.wav' {} \;

# Rename to the original names
rename 's/_/ /g' *.wav

# Make the flacs and remove the waves
flac *.wav
rm *.wav

cd ..
```

---

### Post by mc4man on 2009-03-10
That seemed to work pretty good though I only had one sample high res. flac that I renamed so I could try the batch convert. (It was a 24/88.2 sample

The only 'error' was converting the resampled .wav's back to flac due to them still being 24 bits (though it did convert.

Are you sure you don't want 16/44.1 instead of 24/48

If so change sox to 
```
find . -name "*.wav" -exec sh -c 'sox -S $0 -r 44100 -2 $0.wav && cat $0.wav > $0 && rm $0.wav' {} \;
```

> doug@doug-desktop:~/Desktop/untitled folder$ ~/convertf

flac 1.2.1, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

test 2.flac: done         
test3 1.flac: done         
test.flac: done         

Input File     : './test.wav'
Sample Size    : 24-bit (3 bytes)
Sample Encoding: signed (2's complement)
Channels       : 2
Sample Rate    : 88200

Time: 00:08.99 [00:00.00] of 00:08.99 (100% ) Samples out: 397k  Clips: 0    
Done.

Input File     : './test3_1.wav'
Sample Size    : 24-bit (3 bytes)
Sample Encoding: signed (2's complement)
Channels       : 2
Sample Rate    : 88200

Time: 00:08.99 [00:00.00] of 00:08.99 (100% ) Samples out: 397k  Clips: 0    
Done.

Input File     : './test_2.wav'
Sample Size    : 24-bit (3 bytes)
Sample Encoding: signed (2's complement)
Channels       : 2
Sample Rate    : 88200

Time: 00:08.99 [00:00.00] of 00:08.99 (100% ) Samples out: 397k  Clips: 0    
Done.

flac 1.2.1, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

test 2.wav: wrote 721420 bytes, ratio=0.455
test3 1.wav: wrote 721420 bytes, ratio=0.455
test.wav: wrote 721420 bytes, ratio=0.455
doug@doug-desktop:~/Desktop/untitled folder$ 





---

