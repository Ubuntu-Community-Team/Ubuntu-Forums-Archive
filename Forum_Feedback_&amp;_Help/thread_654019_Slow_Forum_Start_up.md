---
title: "Slow Forum Start up"
date: 2007-12-30
forum: Forum Feedback &amp; Help
---

### Post by pt123 on 2007-12-30
When I open the forum homepage in a new Firefox session it takes 30 seconds to load, and causes Firefox to hang during this period. It is like there are so many javascripts running. But when I open a link to a particular thread in a new Firefox session, it opens in second. 

I have noticed this in the last 2 months.

Can you check some hacker or rogue admin hasn't inserted some devious script in the homepage.


Note. I have a 24Mbit connection.

This is the only script like code I can see is different from the homepage & a thread page
```

<!-- Start Inline Subscription Management -->
<script type="text/javascript">
var threadid = 0;
var imgtag = '';
var subicon = '';

// Update the threadid we're working with
function set_thread(id)
{
	
	threadid = id;
	
}

// Reset the image to subscribed.gif
function reset_image()
{
	imgtag.src = subicon;
}

// Handles the response from the PHP script
function fetch_response()
{

	if (xmlhttp_o.handler.readyState == 4 && xmlhttp_o.handler.status == 200 && xmlhttp_o.handler.responseXML)
	{

		// Format the XML response
		status = xmlhttp_o.fetch_data(fetch_tags(xmlhttp_o.handler.responseXML, 'status')[0]);

		if (status == 'deleted')
		{		
			// Remove the iamge
			var subicon_block = document.getElementById('inline_subs.' + threadid);
			subicon_block.innerHTML = '';
		}

		if (status == 'updated')
		{
			// Display the confirmation image
			subicon = document.getElementById('subicon_' + threadid).src;
			imgtag = document.getElementById('subicon_' + threadid);
			
			subicon2 = subicon.replace(/subscribed.gif/g, 'greentick_small.gif');
			imgtag.src = subicon2;

			// Wait 1 second then change the image back
			var t = window.setTimeout('reset_image()', 1000);
		}

		xmlhttp_o.handler.abort();
	}

}

function update_sub(changeto)
{

	// Setup the Ajax object and handler
	xmlhttp_o = new vB_AJAX_Handler(true);
	xmlhttp_o.onreadystatechange(fetch_response);

	// URL encode the vars (just in-case...)
	threadid = PHP.urlencode(threadid);
	changeto = PHP.urlencode(changeto);

	// Send the data to the php script
	xmlhttp_o.send('ajax.php', 'do=update_subs&changeto=' + changeto + '&threadid=' + threadid);

}

</script>
<!-- End Inline Subscription Management -->

```

---

### Post by heatpumpcontrol on 2007-12-30
same here and different pcs. I've noticed this occurring many times and it even happens on ie4linux too. It causes my FF to hang and I usually just wait till it's over.

---

### Post by p_quarles on 2007-12-30
It loads a lot faster if you close the list of logged in users. Now that an average logged-in user load is around 1,000 at the peak of most days, it would probably make sense to have that closed by default.

As for the devious script hypothesis: that's highly doubtful. All client-side scripting is available for anyone to analyze (it can be obscured, sometimes, but there are always ways of getting around that), and there are enough web developers here that someone would spot it before long.

---

### Post by LaRoza on 2007-12-31
That code is Ajax (Client Side ECMASript that communicated with the server).

It actually would speed up loading times, because it runs after it loads, and won't cause a page to hang.

As for the rogue admin theory, I would bet my life (but not my laptop) that they would never do that.

Try disabling JavaScript to see if there is a difference. It is likely the logged in users.

Try another browser, like Opera, to see if it is universal.

---

### Post by pt123 on 2007-12-31
yes it seems to be fine after minimising/disabling the user list.

---

