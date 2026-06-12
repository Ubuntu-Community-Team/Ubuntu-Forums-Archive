---
title: "FFT of time series in R"
date: 2008-09-28
forum: Education &amp; Science
---

### Post by gvanto on 2008-09-28
Hey I was wondering if anyone has some tips on how to get the FFT
of a simple time series.

I am looking at the Aussie 200 cash future, and its price is in the 5000+ range (attached is prices).

I would like to do FFT on this time series (or of the first hour of trading for example) to see if significant swing components exist in the signal.

Finding it a bit complicated though - in terms of the real and imaginary parts, scaling, frequency range, etc ... Was thinking perhaps to subtract the min. value in the series and then do analysis on that?

help much appreciated
Gerry
FFT newbie

---

### Post by Proton Soup on 2008-09-28
i played around with it a bit since i'm sort of interested in regaining some lost skills.

first caveat, it's been a long time since i've done this, like more than 10 years.  also, i'm using scilab since it's most like what i used to use, matlab.

for starters, i assume you are interested in the series of data that averages about 5000.  that 5000+ is a significant DC (zero frequency) component.  i suggest you start by taking the mean and subtracting it from the series to filter out the DC component.  then, take the fft of that.  what you're left with is complex, of course.  but if you take the absolute value of the complex frequencies, you're left with magnitudes.  and i *think* you're only interested in the first half of the series at this point.  if you plot it out, you will notice it is symmetric.  this has to do with some mathematical properties of the transform.  there's not actually anything going on up in what looks like high frequencies because those are negative and the thing is actually looped back onto itself.

that said, it looks a little boring.  lots of low-frequency action and not much on the high end.  

to get the data in, i loaded your csv file into open office, pasted the series into a text file, and read it with the 'read' function in scilab.

other functions used were 'mean', 'abs', 'fft', and 'plot'.

---

### Post by gvanto on 2008-09-29
Hi Proton Soup :-)

Well I sure am glad that you're getting back into the signal processing after some 'time out' :-)

Thanks for your advice on removing the DC component, I've done it and thinks its looking alot better already.

If scilab is anything like Matlab / R, I'm sure the code below (in R) will make sense ... running it I get the (strange) graph of the fft of the close (price) series for the future (of that file I uploaded before).

I seem to get a 150,000 component at what I (think) is 0 ? (I'm not sure where to get the frequencies for use on the x-axis?)

Do you get a similar graph when using SciLab?

Its pretty bad I used to do DSP while at Uni and now I cant even get the FFT of a simple timeseries ... its a crying shame really!

great day to ya!
Gerry

```


c <- xp$close #assign close series to c
c_ac <- c - mean(c) #subtract DC component

ft <- fft(c_ac) # get FFT
# now this ft series loops onto itself, switch first and second halves:
ft2 = c(ft[8013:16025], ft[1:8012])

barplot(Mod(ft2)) #plot the modulus

```

---

### Post by Proton Soup on 2008-09-29
that looks like what i got.  the first element(what i think is zero) is actually a very small number close to zero, though.  and it should be since that is the DC component.  then a jump up to around 150,000 like yours.  you may get a better idea of what's going on in the graph by either looking at a plot of the first part (say 1:100), or changing the plot axes to log.

---

### Post by gvanto on 2008-09-29
Hey Proton,

Yeah I am a little perplexed by what to use for the x-axis plot. And also the scaling factor - the 150k component doesn't really mean much to me - Any idea to what 

What I am trying to do with this is gauge whether the future is moving simply sideways (weak low-frequency components) or whether it's moving around a lot (trending up and down, resulting in strong low-frequency components).

10Sept (attached - is quite a good example of some areas where it moved sideways alot = from 11:30am to 14:30pm - and other times when it didn't)

the trick is to classify a period as a trending period / not. I'm hoping the fft could provide some insight.

Have you looked at trading systems much Proton ?

ciao
G

---

### Post by Proton Soup on 2008-09-30
no, i haven't really looked into it.  any books to suggest?  i have noticed before that some other things i picked up from engineering like kalman filters and probability show up in economics, but didn't look any further.


about the weights on the frequencies, i think they represent the relative weight of each component.  theoretically, if you add up all the sinusoids (magnitude and phase info), their superposition will be the same time-domain signal you started with.  so, i *think* the 150000 components would be more like 150000/16000.  but i don't remember reconstructing signals that way.  normally, for some kind of signal processing, you just want to get to the frequency domain so that you can easily apply some kind of filter.  and to reconstruct the filtered signal, just do the fft again and there it is.

but, i wouldn't know where to begin wrt to suggesting how to interpret the fft of the close data.  my gut tells me it's a little more complicated than that, and that the volume data has to be factored in somehow.  some type of System Identification seems appropriate, but Lennart Ljung's book was less easy than ffts and even longer ago...

---

### Post by gvanto on 2008-10-01
Hey Proton,

Yeah I have read this one book by Katz & McCormick (Encyclopedia of trading strategies) which discusses low pass filters and wavelets somewhat (their backtesting had mixed success however) but I would like to just do some trend detection for selectively deciding WHEN a trend-following strategy of mine has to run. (ie in a trending period of the day)

About the scaling of the components I'm a little stumped. I think when doing it for a simple sine wave, one divides by 2*pi (pretty good link here [http://zoonek2.free.fr/UNIX/48_R/15.html#2](http://zoonek2.free.fr/UNIX/48_R/15.html#2))

Yeah there's alot of application of filtering and whatnot which applies to economics apparently. 

The volume data can be factored in (its called volume-weighted average price, VWAP) but I thikn the close is sufficient.

reading a article by Ehlers on cycle analysis, will let ya know if it proves any good

Have a great day!
G

---

### Post by Proton Soup on 2008-10-02
thanks, i'll have to see if i can locate a copy of that.

about the scaling, i think it depends, actually.  something i didn't think about until now.  if you look at the [definition of the DFT]("http://en.wikipedia.org/wiki/Discrete_Fourier_transform#Definition") you'll see that they started off with no scaling, and to get back you have to multiply the coefficients by 1/N.  but for practicality, you can spread that scaling out evenly so that the DFT and inverse (IDFT) have the same scaling.  you'd have to look at your own DFT algorithm to see what it is doing.  if you're only interested in the fundamental frequencies involved, you can do what i mentioned earlier and consider [this property]("http://en.wikipedia.org/wiki/Discrete_Fourier_transform#The_real-input_DFT"), and maybe look at Euler's Formula as mentioned there.

your link makes me think of channelingstocks.com  it's a neat idea.  and i can remember looking at [MMM]("http://finance.yahoo.com/echarts?s=MMM#chart1:symbol=mmm;range=my;indicator=volume;charttype=line;crosshair=on;ohlcvalues=0;logscale=on;source=undefined") 5 years or so ago and thinking it would be perfect for this.  for 25 years or so, all it did was go up in a relatively linear fashion.  "all" you had to do was look for a dip below the line to buy, and sell when it overshoots the line.  wash, rinse, repeat.  trouble is, all statistics are a posteriori.  you never know what's going to happen on the next roll of the dice.  and the last 5 years or so it's been flat or trending down, which means you can't just wait it out if you make a bad decision (or maybe you just have to wait a really long time).

but, if that's the route you want to go, you might want to consider looking at the high frequency stuff as "noise".  then, you can run a low-pass filter over the thing and convert it back.  and that's a whole art unto itself because different filters each have their own tradeoffs in how they distort your signal (like say shifting the phase).

hmm, let's see, if it's just the fuzziness on graphs you dislike, you could experiment with the cheap and dirty low-pass filter, the moving average.  and if you choose your weights, you've got an honest-to-dog digital filter (i think you mentioned DSP before).  i think cheap and dirty in the frequency domain would be to just zero out high frequencies and do the IDFT.  not sure how that would screw it up, tho.

or...  plot the real time data and eyeball a curve through it with a red pen.  not very automated, but the wet computer often does things as good or better.

oh, wait, i scrolled down and you link does have moving averages.  yeah, 'smoothing', low pass, whatever you want to think of it as.  and actually, looking further, he's put quite a lot in that page.  you could easily spend a year figuring it out.  some of it looks like maybe just the terminology is changed slightly from similar stuff in DSP or controls, and others like markov chains and wavelets i've never had any experience with at all.

oh, and i almost forgot, there's a free online course on fourier analysis here: [http://see.stanford.edu/SEE/Courses.aspx](http://see.stanford.edu/SEE/Courses.aspx) as mentioned in another thread.  all lectures and course materials including Osgood's own book are freely downloadable. just scrolling through the book will make your eyes glaze over, tho.  it gets fairly deep.

---

### Post by gvanto on 2008-10-02
Hey Proton,

Cool cheers that's alot of info's. 

I have a trend-following futures trading system. The problem is, during choppy sideways (or even not-so-sideways) periods it gets stopped out alot, incurring many small losses.

So the idea with the  frequency detection is to classify the current period we're in as either trending (up until 11:30 on 10Sept for example) / not-trending (11:30 until about 14:30), and consequently turning the system on/off respectively -> or possibly switching to a swing trading system when non-trending period is first detected.

Of course this 'detection' won't go without some lag - as we need to base the analysis on the last 'x' samples or window, by which time, we will have been in this period for x-windows length already. So, some spectral analysis requiring not that many samples (fft requires quite a few, at least 256 i think).

So i am looking at something called MESA by Ehlers at the moment, he's done quite a lot on cycle analysis.

But like you say, one can easily spend a whole year analyzing something like this and try and fine-tune and tweek it. 

Have you given trading a go Mr. Proton Soup?

ciao
G

---

### Post by Proton Soup on 2008-10-02
nah, i get too emotionally involved to trade.

about the fft, you certainly don't need 256 points to use it.  whether what you get is useful or not is another matter.

and, i dunno, some kind of state space solution with a kalman filter might work.  they work really good if you know what the system and the noise is and only require the past N samples for an N-th order system to estimate the state.  you can also set up estimators for the system too, so that it is constantly updating itself.  and, if you want to pretend like you know the future inputs (run a what-if), you can even run one open-loop style and estimate the future (your confidence band can grow wide very fast, tho).

---

### Post by hubie on 2008-10-19
I don't know if you've tried [this software]("http://www.rapidcharting.com/"), but it looks like something you'd be interested in.  I stumbled across it while prospecting through [Freshmeat]("http://freshmeat.net/") for interesting software, and I recalled some of your earlier threads in which I have had the pleasure of participating.

If you give it a go, let me know how it works out because I might want to bump it up my priority queue if it is a neat program.

---

### Post by gvanto on 2008-10-20
hmmm seemingly interesting package : can't tell if it's free or how to use it though.

Have you had a look at QtStalker?

Best,
G

---

### Post by hubie on 2008-10-28
I took a quick stab at how I would do the fft processing on the data you sent.  I've attached a short file that needs to be sourced to run.

---

### Post by gvanto on 2008-10-29
thanks Hubie, had a quick look. Looks pretty cool.

I've kind of given the cycle analysis a break for now. Looking at applying the ADX indicator to classify a price series as trending / not.

So you trading yourself hubie?

thanks again for the great fft file, its good stuff.

Gerry

---

