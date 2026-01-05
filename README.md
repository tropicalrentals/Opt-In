# Opt-In
Website for guest to Opt in to SMS/Email Marketing Campaigns
<!-- Save this as sms-opt-in.html and host it on your domain -->
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Get Guest Updates & Offers</title>
<link rel="stylesheet" href="https://path-to-your-lodgify-css.css">
<style>
  body { font-family: Arial, sans-serif; background: #ffffff; padding: 24px; }
  .form-container { max-width: 500px; margin: auto; padding: 24px; border: 1px solid #ddd; border-radius: 8px; }
  label { display: block; margin-top: 12px; font-weight: bold; }
  input { width: 100%; padding: 10px; margin-top: 6px; border: 1px solid #ccc; border-radius: 6px; }
  button { width: 100%; padding: 12px; margin-top: 16px; background: #007ac9; color: white; border: none; border-radius: 6px; cursor: pointer; }
  button:hover { background: #005999; }
  .consent { margin-top: 14px; font-size: 14px; }
</style>
</head>
<body>

<div class="form-container">
  <h2>Receive Exclusive Guest Updates & Offers</h2>
  <p>Opt in to receive local tips, property info, and special offers during your stay.</p>

  <form id="smsForm">
    <label>Your Full Name</label>
    <input type="text" name="name" required />

    <label>Mobile Number</label>
    <input type="tel" name="phone" placeholder="+1 555 555 5555" required />

    <div class="consent">
      <input type="checkbox" id="consentCheck" required>
      <label for="consentCheck">
        I agree to receive recurring SMS messages from Tropical Rentals FL. Message frequency varies. Message & data rates may apply. Reply STOP to opt out, HELP for help.
      </label>
    </div>

    <button type="submit">Yes, Send Me Offers</button>
  </form>

  <div id="thanks" style="display:none; margin-top:20px; color:green;">
    Thank you! You’re now opted in.
  </div>
</div>

<script>
document.getElementById('smsForm').addEventListener('submit', async (e) => {
  e.preventDefault();
  const data = {
    name: e.target.name.value,
    phone: e.target.phone.value,
    consentTimestamp: new Date().toISOString()
  };
  await fetch('/api/subscribe', {
    method: 'POST',
    headers: {'Content-Type':'application/json'},
    body: JSON.stringify(data)
  });
  e.target.style.display = 'none';
  document.getElementById('thanks').style.display = 'block';
});
</script>

</body>
</html>

---

## 📝 SMS Opt-In Flow

1. Guest visits the SMS opt-in page
2. Guest enters phone number and checks consent box
3. Consent is stored with timestamp and IP address
4. Phone number is eligible for SMS messaging
5. Messages are sent via Twilio Messaging Service

---

## 📜 Consent Language (Required)

The following consent language is displayed on the opt-in page:

