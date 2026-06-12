---
title: "Octave error:&quot;error: can't perform indexing operations for &lt;unknown type&gt; type &quot;"
date: 2008-10-30
forum: Education &amp; Science
---

### Post by smattiuz on 2008-10-30
I get this error 
> error: can't perform indexing operations for <unknown type> type


while running this code

array --> uses array.m file to allocate an array with 5000 0<=integers<=9

B=[0]; --> allocates my result array

```

resto=0;
tic
for i=1:1:length(A)
	B(1)=+A(i);
        if B(1)>9
	  if length(B)==1
	     B(2)=0;
          end
	  B(2)=+1;
          B(1)=-10;
          k=2;
          while B(k)>9
	     if (length(B)==k)
	       B(k+1)=0;
             end
	     B(k+1)=+1;
             B(k)=-10;
             k=k+1;
          end
        end
end
toc

```

this script is like a counter, adding one on one the 5000 numbers in the A matrix to the B(1) cell of the array and checks if this number is >9. In this case it put in B(k) the remnant, and B(k+1) is increased by one

ex. 
B(1)=9, Adding 3 -> B(1)=12.
B(1)=2 B(2)=1

so this is like the result number (ex 12) is putted reversed in the array (21)
since everytime it checks if there's the next cell (i'm supposing that the only way the next cell cannot exist is when my counter is in the last position of the B array), if not i create a B(k+1)=0 cell, so i'm sure i have a new cel which i can add +1 furthermore.

So where's my problem? (except my non-optimized code)

---

### Post by ofri on 2009-01-27
you are probably running [PHP]array.m[/PHP]. use [PHP]array[/PHP] instead.

---

