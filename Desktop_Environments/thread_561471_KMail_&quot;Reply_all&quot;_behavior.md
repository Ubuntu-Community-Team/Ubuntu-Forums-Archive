---
title: "KMail &quot;Reply all&quot; behavior"
date: 2007-09-27
forum: Desktop Environments
---

### Post by Xianath on 2007-09-27
Greetings all.

When replying to all, KMail places the original sender in To: and all recipients in CC: I haven't seen any other mail client do that, even my cell phone preserves To: and CC: when replying to all. At first I thought it was a bug but then I saw this:

```

**    // merge To header and CC header into a list of CC recipients**
    if( !cc().isEmpty() || !to().isEmpty() ) {
      QStringList list;
      if (!to().isEmpty())
        list += KPIM::splitEmailAddrList(to());
      if (!cc().isEmpty())
        list += KPIM::splitEmailAddrList(cc());
      for( QStringList::Iterator it = list.begin(); it != list.end(); ++it ) {
        if(    !addressIsInAddressList( *it, recipients )
            && !addressIsInAddressList( *it, ccRecipients ) ) {
          ccRecipients += *it;
          kdDebug(5006) << "Added " << *it << " to the list of CC recipients"
                        << endl;
        }
      }
    }

```

Apparently this is by design. Not sure if this is universal, but at least in my environment To: indicates people directly involved and CC: indicates people "in the loop." When people get hundreds of emails a day, they want to make sure those that directly concern them are prioritized. I have had, on more than one occasion, seen the above behavior affect my work and in fact the company's business just because I overlooked changing one of the CC: recipients to To:

My question is, is this bothering anyone else but me? If it is a concern to enough people, I'll log a feature request upstream and post it back here so people can vote for it. If there's no interest, I'll just patch my local copy as it is certainly a problem for me.

Thanks,
Peter

---

### Post by rax_m on 2007-09-28
While I don't use Kmail.. I agree that it should preserve the To and CC fields as in the original email. It definitely makes a huge difference when sending or receiving hundreds of emails a day. 

Might be worth filing a bug reprort.. if you haven't already. 

Rax

---

