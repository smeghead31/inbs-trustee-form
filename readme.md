# Charity Trustee Details form — deployment notes

Files in this folder:

| File | Purpose |
|---|---|
| `index.html` | The form your team completes |
| `thanks.html` | Confirmation page shown after a successful submission |

Keep both files in the same folder. Do not rename `index.html`.

## 1. Deploy to Netlify

**Drag and drop:** sign in to Netlify, go to **Sites**, and drag this whole folder (or the `.zip`) onto the drop area. Netlify publishes it and gives you a URL such as `https://random-name-1234.netlify.app`. Rename the site under **Site configuration → Site details → Change site name** to something like `ricruden-trustee-form`.

**Git:** push the folder to a repository and connect it in Netlify. No build command, publish directory `/`.

## 2. Switch on form handling

The form uses Netlify Forms. Detection happens at deploy time from the `data-netlify="true"` attribute in `index.html`.

1. In the Netlify site, open **Forms**. After the first deploy you should see a form named **charity-trustee-details**.
2. If it does not appear, check **Site configuration → Forms** and confirm form detection is enabled, then redeploy.
3. Submit the form once yourself to confirm the whole route works.

## 3. Get submissions emailed to you

**Forms → charity-trustee-details → Settings and usage → Form notifications → Add notification → Email notification.** Enter your address. Each submission then arrives as an email with every field listed, and is also stored in the Netlify dashboard where it can be exported to CSV.

Netlify's free tier includes 100 form submissions per month. Above that you need a paid Forms plan.

## 4. Spam and privacy

- A hidden honeypot field (`bot-field`) is already wired in, so no CAPTCHA is needed.
- The form collects home addresses and dates of birth. Give the site URL only to the people who need it, and delete submissions from the Netlify dashboard once the details are recorded in OSCR OnlineServices.
- Netlify stores submissions on its own servers. If that is not acceptable for personal data of this kind, an alternative is to have people use the **Print or save as PDF** button and return the file by email instead.

## What the form does

- Individual or corporate trustee toggle — swaps the name fields to suit.
- "Do you live outside the UK?" — set to Yes and a country field appears; UK postcode validation is relaxed.
- Exemption intent — set to Yes and a short reason box appears.
- Date of birth capped at 16 years ago; appointment date cannot be in the future.
- Phone numbers have spaces and brackets stripped automatically; postcodes are upper-cased.
- The declaration tick box is mandatory and mirrors the four OSCR acknowledgements.

To change any wording, edit `index.html` in a text editor and redeploy.
