---
title: "What's up with PayPal and Konqueror?"
date: 2005-05-07
forum: Desktop Environments
---

### Post by tomchuk on 2005-05-07
So I went to Log into my PayPal account for the first time in over a year tonight, only to be surprised with a message saying that the IP address of the host (102.112.2O7.net) doesn't match the one the cert was issued to. Note that that domain is 2, the letter 'O', and 7.net not 207.net.

So I check out the source, everything is coming from the real PayPal site except for a 1x1px gif at the bottom of the page:
```

...
</div>
<br>
</div>
<img height="1" width="1" src="https://102.112.2O7.net/b/ss/paypalglobal/1/G.4--NS/594536713?pageName=Welcome::p/wel/index-outside::&amp;c7=Unknown&amp;c8=Unknown&amp;c9=Unknown&amp;c10=US&amp;c12=Unknown" border="0" alt="">
</body>
</html>

```
This happens even when Konq identifies itself as IE under Windows or Mozilla under Linux or Windows.

Here is what Firefox and w3m return for comparison:
```

...
</div>
<br>
</div></body>
</html>

```

This tracking image is even added to the non-ssl pages under Konqueror, and using tethereal to compare the traffic as it comes down the wire verifies that w3m and Firefox are getting the proper page and Konq is still getting the affected page.

Anyone have any idea of what's going on?

---

