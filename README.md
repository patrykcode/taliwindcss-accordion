```
document.addEventListener("DOMContentLoaded", () => {
    accordion();
});



function accordion() {
    const elements = [...document.querySelectorAll(".accordion > div")];
    const last = {};
    for (let i = 0; i < elements.length; i++) {
        const id = elements[i].id || false;
        const parent = elements[i].getAttribute("data-parent") || ".accordion";
        last[parent] = null;
        if (id && parent) {
            document.querySelector("#" + id + " .header-title").onclick =
                function () {
                    if (last[parent] !== this) {
                        accordionCloseAll(parent + ">div");
                    }
                    accordionOpen("#" + id);
                    last[parent] = this;
                };
        }
    }
}

function accordionOpen(selector) {
    const element = document.querySelector(selector);
    if (element) {
        element.classList.toggle("show");
    }
}

function accordionCloseAll(selector) {
    const elements = [...document.querySelectorAll(selector)];
    for (let i = 0; i < elements.length; i++) {
        if (elements[i]) {
            elements[i].classList.remove("show");
        }
    }
}
```
