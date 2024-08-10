# scheduling-automation-app

In this challenge we’re going to build a simplified version of one. We’ll query one or more calendars to find out when you are free, then strip out times when you’ve said you’re not and offer up the remaining time slots to be booked. Then we’ll create the event in your calendar.

So how can we do this? Well both Google and Apple support a common API called CalDAV. CalDAV is an extension of WebDAV that provides a standard for clients to access calendar information on a remote server. It is defined in RFC 4791 and updated by RFC 5689, RFC 6638, RFC 6764, RFC 7809, RFC 7953, RFC 8996.

You can find details of Google’s CalDAV API here. Google also provides it’s own API. It doesn’t appear that Microsoft supports CalDAV, instead it provides it’s own Outlook calendar API, details here. Apple doesn’t appear to have any documentation for it’s CalDAV API.

Step Zero

In this step you decide which programming language and IDE you’re going to use and you get yourself setup with a nice new scheduling app project. You might want a web-friendly stack if you fancy building a web based solution like the examples above. Otherwise you could build a CLI or desktop application. The choice is yours!

Once you’ve done that you might like to create a Google Account, Microsoft Outlook Account or iCloud Id if you don’t have one, or want to use a different one for testing.

Step 1

In this step your goal is to authenticate with the calendar API. Google details how to setup authorisation in their Quickstart Guide. We’ll focus on Google for this challenge.

Microsoft’s Quickstart also takes you through getting a Client Id but you need a Work or School account to access it.

Step 2

In this step your goal is to get a list of events from the calendar.

You’ll need to get an OAuth 2.0 token from Google. You can then make a GET request to https://apidata.googleusercontent.com/caldav/v2/><cal_id>/events to get the list of events. Be sure to replace <cal_id> with your calendar id, which is your email address.

You should parse the response and build a sensible list of events. Now would be a good time to define an Event data type.

I found it useful to use Postman to test the API first. You’ll need to configure it to use OAuth 2.0 and set the scope to be: https://www.googleapis.com/auth/calendar

Step 3

In this step your goal is to create a consolidated calendar. In other words pull in events from more than one calendar, i.e. a work and personal calendar. You should consolidate the list of events and extend the Event data type to identify the type of the event.

Step 4

In this step your goal is to allow the user to configure a predefined availability window for each day of the week. For example to say that they’re available for book events from 08:00 to 17:30 Monday to Friday, but not available at the weekend.

You should then combine this with the list of events in their calendar(s) to determine when they are free within the availability window.

Then allow the person booking an event to specify an event duration and select a time slot that is free for at least that duration.

Step 5

In this step your goal is to create an event in the calendar, you should include the list of attendees so they also get an invite sent to them. This will require you to ask the person booking the event for their name and email address. You will find Section 5.3.2 of the RFC useful.

If you want to take this even further check out the [cal.com GitHub Repo](https://github.com/calcom/cal.com) and consider contributing a bug fix or extending the functionality. They currently have a job open and offer a paid bounty for some of the open source contributions - see [here](https://cal.com/jobs).
