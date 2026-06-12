---
title: "Text lost upon &quot;Submit Reply&quot;"
date: 2011-04-08
forum: Forum Feedback &amp; Help
---

### Post by Doug S on 2011-04-08
I had a situation where I was adding a "New Reply" to a thread. When I "clicked" on the "Submit Reply" button, the resulting post had deleted most of my text.
I am wondering if this is a bug or just one of those unexplained things that happened. Normally what I would do in such a situation is try to repeat the event, to determine if it is reproducible or not. If not reproducible, then so be it. However, I think it would be inappropriate for me to be doing test posts on these live forums, trying to isolate what may or may not be some bug.
From past postings, I already know that certain character sequences can get turned into little icon things, for example a happy face, and I have had to edit the post to repair it. I am wondering if there is a character sequence that indicates EOF (End Of File) or something. I did search around this forum for any other threads about lost text. I also tried to find information about special character sequences. I apologize if this information is somewhere obvious and I just didn't find it (I did find the BB Code pages).
I am asking for advice on how to proceed, or if I should even try to go further.
Other information:
I have the raw packets that were sent upon clicking "Submit Reply".
I am reasonably certain I could re-create the exact same text.
The text that was lost began at a hyperlink (I wasn't trying to include hyperlink, but my typing turned into a hyper link).
 
Edit: Sorry for using the wrong font size. I was not aware that I was not using the default. I also now realize that I have done several postings with not default font size. I will go back and fix them. The "New Reply" to which this thread refers, was all typed (not cut and pasted) in the reply box, and was at the default font size (as far as I know).

---

### Post by Doug S on 2011-04-18
I have continued to search for the interpretations of special character sequences and not found any list. I know for sure that "8 )" without the space will get converted to a yellow circle face type icon. I also searched the generic vbulliten and special characters and character sequences. The only thing I found was that e-acute ( hex E9 ) can cause all following text to be truncated. However that was not in my original text stream.
 
I guess I have the option to make a change in - "User Control Panel - Edit Options - Miscellaneous Options - Message Editor Interface" to not use the WYSIWYG type editor.
 
Also, I now try to actually edit in something else and cut and paste the final text into the Reply to Thread window, so that if it  gets lost upon "Submit Reply" I still have it.
 
Below is an excerpt from my original loss of text "Submit Reply" issue packet:
>  
... to+connect+to+a+share+via+%3CA+href%3D%22file%3A%2F%2F%5C%5C10.0.0.1%5C%22%3E%5C%5C10.0.0.1%5C%3C%2FA%3E.+My+thinking+ ...


Below is an expert from the resulting post:
>  
... to connect to a share via</div>

 
So, I still wonder if I can repeat the issue, or if it was just one of those one of those things. Following are two things: first just try to re-create the issue; Second some following text, just to see if is actually gets posted.
 

... to connect to a share via

---

