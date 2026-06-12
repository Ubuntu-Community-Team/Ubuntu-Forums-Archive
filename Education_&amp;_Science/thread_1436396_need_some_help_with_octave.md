---
title: "need some help with octave"
date: 2010-03-22
forum: Education &amp; Science
---

### Post by clapton on 2010-03-22
Hello people!

I'm trying collect a data from a cvs file.
But I can't run plot. 

I'm noob at octave, I'm a ex matlab user.

```
clear
clc
[ndata, headertext] = xlsread('Data100M_11.csv', 'sheet1');

[a,b]=size(headertext);

text = headertext(1,:); %save strings from LSD Header
data=headertext(2:a,:) %data from LSD res file

[c,d]=size(data)

k=1:1:c; %creates a K vector to discrete time steps
x1=(data(:,1)) %assign to x1 first column from file

%plot() %I wanna plot, I don't know how... I think is because it's a cell array?!

```
(file in attach)

---

### Post by omeliok2010 on 2010-03-22
> **clapton said:**
> Hello people!

I'm trying collect a data from a cvs file.
But I can't run plot. 

I'm noob at octave, I'm a ex matlab user.

```
clear
clc
[ndata, headertext] = xlsread('Data100M_11.csv', 'sheet1');

[a,b]=size(headertext);

text = headertext(1,:); %save strings from LSD Header
data=headertext(2:a,:) %data from LSD res file

[c,d]=size(data)

k=1:1:c; %creates a K vector to discrete time steps
x1=(data(:,1)) %assign to x1 first column from file

%plot() %I wanna plot, I don't know how... I think is because it's a cell array?!

```(file in attach)
We used a variable-sized headline style for our ads in the '90s. It was a PITA to get the copywriters to give us headlines that worked. We typically used two different sizes in the heds, but the key in compositing was using LOTS of negative space.

---

### Post by carandraug on 2010-03-23
> **clapton said:**
> Hello people!

I'm trying collect a data from a cvs file.
But I can't run plot. 

I'm noob at octave, I'm a ex matlab user.

```
clear
clc
[ndata, headertext] = xlsread('Data100M_11.csv', 'sheet1');

[a,b]=size(headertext);

text = headertext(1,:); %save strings from LSD Header
data=headertext(2:a,:) %data from LSD res file

[c,d]=size(data)

k=1:1:c; %creates a K vector to discrete time steps
x1=(data(:,1)) %assign to x1 first column from file

%plot() %I wanna plot, I don't know how... I think is because it's a cell array?!

```
(file in attach)

Eheheh, olha um companheiro de Braga!

Hi

I also started using octave recently. Maybe I could help but you don't say what you are trying to plot. Your code only plays around with the text extracted from the xls file, not with any numbers. Basically,plot works

```
plot (xData, yData)
```

I think in your case

```

plot(k, ndata(:,1))  #this should plot m_cmax
plot(k, ndata)       #this will plot all columns

```

Run 'help plot' to see how it works

You could also try the [octave help mailing list]("http://www.gnu.org/software/octave/archive.html"). They are very helpful.

---

### Post by Finder9 on 2011-03-11
Hi,
Is this the right place to post a question about trying to run Octave within Cygwin?  Scripts will run, but (new) functions do nothing but display ">" in place of the Octave prompt.  This seems to be in some kind of editing mode (from which there's no obvious escape).  What to do?
Finder9

---

### Post by carandraug on 2011-03-11
> **Finder9 said:**
> Hi,
Is this the right place to post a question about trying to run Octave within Cygwin?  Scripts will run, but (new) functions do nothing but display ">" in place of the Octave prompt.  This seems to be in some kind of editing mode (from which there's no obvious escape).  What to do?
Finder9

Hello Finder9

I don't think this is the right place if it's Cygwin specific. Try asking in the octave help mailing list (help@octave.org), some people there use it in cygwin. See this page [on their homepage]("http://www.gnu.org/software/octave/help.html").

---

