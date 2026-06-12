---
title: "Learning Matlab"
date: 2012-09-29
forum: Education &amp; Science
---

### Post by Hal Jordan on 2012-09-29
Hi, it's my first time on these forums. I've used Ubuntu before but my question today isn't about Ubuntu, it's about Matlab. I read somewhere that all kinds of languages are discussed on these forums so I decided to try my luck here. My instructor assigns such long projects every week that are very time-consuming but does not really take the time to explain the subject. 

I want to write a program that plots one peicewise function 
f(t) = -Pi*t on &#8722;1 &#8804; t &#8804; 0 and Pi*t on 0 < t &#8804; 1 and one Fourier Series F(t) = Pi/2 - 4/Pi Sum[(1/2k+1)*Pi*t*cos(2k-1)] k = 1 to Infinity on &#8722;1 &#8804; t &#8804; 1 using the fplot command. It's only my fourth assignment using Matlab so it's a bit of a jump going from one plot to two or more on the same graph. I wanted to show that I made an attempt at the problem so here is my code so far:


function Ft = Fourier(t)
% Ft = Fourier(t)
% INPUT  
%  t: Values between -1 and 1 
%
% OUTPUT  
%  Ft: Fourier approximation 
%
a=(0:9);
n=numel(a);
term(i)=1./(((2.*a(i)-1.^2)).*cos ((2.*a(i)-1)).*pi.*t);
[x,y]=fplotf(Ft,[-1,1])
plot(x,y)
end


Any help would be appreciated.

---

### Post by zgornel on 2012-10-02
I did not check what your program should do - probably it prints a function in [-1 1] and then, some of its harmonics ...

Here's the code (it MIGHT help if you check the documentation of fplot carefully ;) )

```

function run_this_thing % the main function
    t = [-1 1];         % define f,F interval
    fh = @FT;           % function handle
    fplot(fh, t);       % do the plot
end

function Y = FT(t)       % vectors to plot in
Y(:,1) = sign(t(:)) * pi;% this is f(t)
for k = 2: 1: 10         % number of k's ...
    Y(:,k) = pi/2 - 4/pi*sum((1/2*k+1)*pi*t*cos(2*k-1)) ; % this is F(t)              
end

end

```

---

