---
title: "time-domain signal in MFCC"
date: 2013-07-05
forum: Education &amp; Science
---

### Post by SkyLight196 on 2013-07-05
I have read about MFCC and Speech Recognition, and I don't understand one point. According to the document in this page [http://practicalcryptography.com/miscellaneous/machine-learning/guide-mel-frequency-cepstral-coefficients-mfccs/](http://practicalcryptography.com/miscellaneous/machine-learning/guide-mel-frequency-cepstral-coefficients-mfccs/), what is the "time-domain signal"?? Is that the float number in data sub-chunk which I read in header-file of a wave file?
  P/s: Sorry for my poor English :D

---

### Post by xytron on 2013-07-10
> **SkyLight196 said:**
> what is the "time-domain signal"?? 
  P/s: Sorry for my poor English :D

The easiest way to see how something changes with time (a time series) is to make a graph.

The time domain signal in that document is  s(n).  That just says that s is function of n.  It's  simply a variation of your signal at each time n.

n is the abscissa  (horizontal). The ordinate  (y value) will usually represent  the wave height (amplitude). Such a plot is in the so called time domain.


Signals can be also be represented as a sum of many sine waves with different  amplitudes and frequencies. 
So we could make a second plot.

The different sine wave components (harmonics) represent the frequency representation of your signal.
 
Here the abscissa would be the wave frequency and the ordinate some parameter related to the wave amplitude.  This second plot would be in the so called frequency domain.

---

