# Already Taken

**An experiment by The Wavestate Project on the social and economic implications of artificial intelligence.**

Every day, someone posts something like this: *"Looking for a photographer. I really need new headshots."*

Right next to that post is their profile picture. It's a photo of their face, one they chose, and it's already doing the job a headshot does.

Already Taken is a bot that finds those posts. It takes the picture the person already shows the world, turns it into a studio-quality portrait with AI, and replies with it. It's free, it's instant, and nobody asked for it.

Then it listens to what happens next.

---

## Why this exists

Already Taken is two things at once, and it's meant to be uncomfortable to hold both.

**It's a gift.** A lot of people need a good headshot: for a job application, a LinkedIn profile, a speaker bio, a dating profile, a first impression they don't get to redo. A professional session often costs a few hundred dollars, plus the time to book it, show up, and sit in front of a stranger. Plenty of people don't have the money, the time, or a photographer they trust. For them, this is a decent portrait for nothing, delivered in the same thread where they asked.

**It's a question.** Your face is about as close to *you* as anything gets. A portrait has always meant someone actually looked at you: a person, a camera, a moment that really happened. Now a machine can make a convincing one from a thumbnail, without you in the room. And the person asking for a photographer was holding the raw material the whole time. They were looking for something that, in a sense, already existed.

So is this help, or is it an intrusion? Both? Does the answer change depending on who you ask?

That's what we want to find out.

## How it works

1. **It looks.** The bot searches Bluesky for recent public posts where people say they're looking for a portrait or headshot photographer.
2. **It checks.** Before doing anything, it asks Google's Gemini AI two questions. Is this person really asking for portraits of themselves, and not, say, a photographer advertising? Is their profile picture a real photo of one adult? If either answer is no, it moves on.
3. **It relights.** It sends the profile picture to Gemini with instructions to make a professional portrait (studio backdrop, good lighting, head and shoulders) while keeping the person exactly who they are. Same face, same features, same skin tone, same age. No slimming, smoothing, or "improving."
4. **It replies.** It posts the portrait as a public reply to the original post, with a short note and an image description that says it was made by AI.
5. **It listens.** It reads every reply to its portraits and has Gemini sort them by reaction: grateful, amused, curious, uneasy, offended, declining on principle, or a photographer pushing back. Then it writes a plain-language summary of the whole conversation.

Everything runs in a single web page, `index.html`. There's no server and no database. The portraits exist only in the replies.

## What we're trying to learn

**What do people do when the thing they asked for shows up, made by a machine?** Say thanks? Laugh? Feel seen, or feel watched?

**Who refuses, and why?** Some people will turn down a good, free thing on principle. We want to understand that choice instead of dismissing it, whether it comes from consent, honesty, wanting a real person behind the camera, or standing with photographers. Refusing is a real response to technology, and maybe the most interesting one.

**Does it split by generation?** People who grew up with filters and avatars may already treat an edited face as a normal face. People who grew up with film may see a photo as proof that something happened. That's a hunch, not a finding. The bot only counts someone's generation when they say it themselves. It never guesses from a face.

**What happens to the work?** If a decent portrait costs nothing, what is a photographer actually paid for? Maybe it was never just the picture. Maybe it's direction, trust, and the experience of being seen by another person. We want to hear from photographers directly.

**Where's the line between "a better picture of me" and "not me"?** Everyone already curates their face online. At what point does a portrait of you stop being yours?

## Yes, we use AI to understand the response to AI

The listening half of the experiment is done by AI too. Gemini sorts the replies and summarizes the conversation. That's on purpose, and it's part of the same question: we're asking a machine to read how people feel about machines.

Its reading can be wrong, flat, or biased. So every tagged reply links back to the original post, and the raw data can be downloaded for anyone who'd rather read it themselves.

## Ground rules

We know this is pushy. Nobody asked for an AI portrait, and that's part of what's being tested. These limits exist because of it.

- **Only what's already public.** The bot uses the profile picture people chose to show the world, and it only replies to public posts.
- **You stay you.** The AI is told to keep identity exactly and never change bodies, age, or features. It relights and restages. It doesn't redesign.
- **Always labeled.** Every portrait's image description says it was made by AI from the person's profile picture.
- **Adults only.** Anyone who looks under 18 is skipped.
- **Once.** One portrait per person per 30 days, and a daily limit on total replies.
- **Nothing kept.** The page keeps no copies of the portraits. It only remembers which posts it has answered, so it doesn't repeat itself. Downloaded research data replaces everyone's name with an anonymous id.
- **Easy out.** If you got a portrait and want it gone, reply or message the account and we'll take it down.

## What are we all gonna do?

This is the part without an answer.

The ability is already here. Anyone with a phone can turn a selfie into a polished portrait in seconds. Nobody voted on that. It just arrived. So each of us gets to decide, mostly on our own, how to respond: use it, ignore it, refuse it, be angry about it, or make art about it.

There's no consensus yet. Two instincts do keep coming up. People tend to be far more comfortable using AI on their own image than having it done to them. And people want to know when they're looking at something a machine made. Consent and honesty keep showing up as the dividing lines. Past that, it gets messy fast.

Already Taken walks straight into that mess. It does something useful that nobody asked for, with something as personal as a face, and then asks the people on the other end what they think. Their answers are the actual artwork.

Maybe the result is gratitude. Maybe it's a line drawn in the sand. Probably it's both, from different people, for reasons worth hearing.

Either way, we're all going to have to decide what we still want to do ourselves, and what we're willing to let be already taken.

---

## Run it yourself

You need:

- A Bluesky account for the bot. Use a separate one and say it's automated in the bio. Create an app password under **Settings → Privacy and security → App passwords**.
- A Gemini API key from Google AI Studio.
- Chrome or another modern browser.

Then:

1. Download `index.html` and open it, or serve this repo with GitHub Pages and open that link.
2. Sign in, add your Gemini key, and adjust the search phrases.
3. Start in manual mode. Search, make a few portraits, and look at them before posting anything.
4. When it's behaving the way you want, turn on auto-run. It only runs while the tab is open.
5. Come back to **Responses** to read what people said, get a summary, or download the data.

If your browser blocks requests when you open the file directly, run `python3 -m http.server` in this folder and visit `http://localhost:8000`.

Your keys stay in your browser. The page only talks to Bluesky and Google's Gemini API.

## Credits

Already Taken is an experiment by **The Wavestate Project** on the social and economic implications of artificial intelligence. It's built on Bluesky's open AT Protocol and Google's Gemini models.
