### 📘 **1. Project Overview**

**Project Name:** Personal Portfolio Website
**Purpose:**
Ye website ek personal portfolio hai jo aapke skills, education, experience aur projects ko showcase karti hai.
Iska use job applications, freelancing profiles, aur personal branding ke liye hota hai.

### 🌐 **3. Technologies Used**

| Technology             | Purpose                                                  |
| ---------------------- | -------------------------------------------------------- |
| **HTML5**              | Page structure aur content define karne ke liye          |
| **CSS3**               | Website ko style aur design dene ke liye                 |
| **JavaScript**         | Tabs, mobile menu, aur form submission ke liye           |
| **Font Awesome**       | Icons ke liye (social media, menu icons, etc.)           |
| **Google Apps Script** | Contact form data ko Google Sheet me store karne ke liye |

---

### 🧩 **4. HTML Structure (index.html)**

#### 🔹 **Header Section (`#header`)**

* Contains **navigation bar** and **intro text**.
* Navigation menu links: Home, About, Services, Portfolio, Contact.
* Mobile menu ke liye icons: `fa-bars` (open), `fa-circle-xmark` (close).

#### 🔹 **About Section (`#about`)**

* Two columns:

  * **Left:** Profile Image
  * **Right:** About Text + Tabs (Skills, Experience, Education)
* Tabs ke liye JavaScript se switching hoti hai.

#### 🔹 **Services Section (`#services`)**

* Three service cards:

  * Web Designing
  * UI/UX Designing
  * App Designing
* Hover effect lagaya gaya hai (`background: #ff004f` on hover).

#### 🔹 **Portfolio Section (`#portfolio`)**

* Three project samples:

  * Social Media App
  * Music App
  * Online Shopping App
* Hover karne par overlay layer show hoti hai (`.layer`).

#### 🔹 **Contact Section (`#contact`)**

* Two columns:

  * **Left:** Contact info + social media icons + CV Download button.
  * **Right:** Contact form connected to Google Sheet.

#### 🔹 **Footer (`.copyright`)**

* Simple copyright

  * `© Vipin. Made with ❤️ by Vipin Maurya`

---

### 🎨 **5. CSS Explanation (style.css)**

#### 🧱 **Base Styling**

```css
* {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  box-sizing: border-box;
}
body {
  background: #080808;
  color: #fff;
}
```

* Sets dark background and white text for elegant contrast.

#### 🔹 **Navigation Bar**

* Uses `flexbox` for alignment.
* Menu links have red underline effect on hover (`::after` pseudo-element).

#### 🔹 **Header Text**

* Large title and colored span for name emphasis (`color: #ff004f`).

#### 🔹 **About Section Tabs**

* `active-tab` and `active-link` classes used to switch visibility of tab content.

#### 🔹 **Services & Portfolio**

* Uses CSS **Grid layout** (`grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))`)
* Adds hover transition and scaling effect for animation.

#### 🔹 **Contact Form**

* Custom styled form inputs, textarea, and buttons.
* Green success message (`#msg`) appears after form submission.

#### 🔹 **Responsive Design (Media Query)**

```css
@media only screen and (max-width: 600px)
```

* Mobile menu slides in from right.
* Text size and layout adjust for small screens.

---

### ⚙️ **6. JavaScript Functionality**

#### 🔸 **(A) Tab Switching (Skills / Experience / Education)**

```js
function opentab(tabname){
  for(tablink of tablinks){ tablink.classList.remove("active-link"); }
  for(tabcontent of tabcontents){ tabcontent.classList.remove("active-tab"); }
  event.currentTarget.classList.add("active-link");
  document.getElementById(tabname).classList.add("active-tab");
}
```

👉 This enables switching between tab content dynamically.

---

#### 🔸 **(B) Mobile Menu Open/Close**

```js
function openmenu(){ sidemeu.style.right = "0"; }
function closemenu(){ sidemeu.style.right = "-200px"; }
```

👉 Works with hamburger (`fa-bars`) and close (`fa-circle-xmark`) icons.

---

#### 🔸 **(C) Contact Form → Google Sheets Integration**

```js
const scriptURL = 'https://script.google.com/macros/s/AKfycby7drJr3O8VLujWYTfzskB0LdTEqfPngd5DberpKovGfKZ0sGMlBjsUpbh8fkbhzbwXPw/exec'
const form = document.forms['submit-to-google-sheet']
const msg = document.getElementById("msg")

form.addEventListener('submit', e => {
  e.preventDefault()
  fetch(scriptURL, { method: 'POST', body: new FormData(form)})
    .then(response => {
      msg.innerHTML="Message sent successfully..."
      setTimeout(()=>{ msg.innerHTML="" }, 5000)
      form.reset()
    })
    .catch(error => console.error('Error!', error.message))
})
```

👉 When user submits the form, data is sent to Google Sheet using **Google Apps Script**.

---

### 📱 **7. Features Summary**

✅ Responsive design (works on mobile & desktop)
✅ Animated transitions & hover effects
✅ Interactive tabs
✅ Functional contact form
✅ Font Awesome icons
✅ Downloadable CV button

---

### 🚀 **8. Future Improvements (Suggestions)**

* Add **scroll animations (AOS.js or Framer Motion)**
* Use **dark/light mode toggle**
* Add **project links (GitHub / Live Demo)** in portfolio
* Improve **SEO meta tags** and **favicon**

---

### 🧩 **9. Output Preview (Structure-wise)**

| Section   | Description                                    |
| --------- | ---------------------------------------------- |
| Header    | Welcome intro + navigation                     |
| About     | Profile + tabs (skills, experience, education) |
| Services  | 3 service cards with hover animation           |
| Portfolio | 3 project previews with overlay                |
| Contact   | Form + social icons + CV download              |
| Footer    | Copyright                                      |



