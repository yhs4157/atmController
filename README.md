가상 데이터

const card = {
id: string,
PIN: string,
accounts: [
{
id: string,
name: string,
balance: Number,
},
]
}

const root = document.getElementById("root");

const card = {
id: '123456789',
PIN: '1111',
accounts: [
{
id: 'aaaaa',
name: 'aaaa',
balance: 1000,
},
{
id: 'bbbb',
name: 'bbbb',
balance: 500,
}
]
}
// example

const pin = document.querySelector('#pin-form')
const pin_input = document.querySelector('#pin-form input')
const pin_button = document.querySelector('#pin-form button')

password_unlock = false;
// 패스워드 성공여부 확인

function onSubmitTest(e) {
e.preventDefault();
const value = pin_input.value;
if(card.PIN === value) {
password_unlock = true;
}
selectAccount()
}

pin.addEventListener("submit", onSubmitTest)

const account = document.getElementById('account');

const selectAccount = () => {
if(!password_unlock) return;
console.log(account.classList)
account.classList.remove('none')
for(ele of card["accounts"]) {
const btn = document.createElement('button');

        btn.textContent = ele.name;
        btn.id = ele.id
        btn.addEventListener("click", onClickBtnAccount);

        account.appendChild(btn);
    }

}

const onClickBtnAccount = (e) => {
e.preventDefault();
console.log(e.target)

    for(ele of card["accounts"]) {
        if(ele.id === e.target.id) {
            account.classList.add('none')
            show(ele)
        }
    }

}

const show = (ele) => {
// 계좌 특정화
console.log(ele)
const balance = document.createElement('div')
balance.textContent = ele.balance;

    const input_money = document.createElement('input');

    const btn_withdraw = document.createElement('button');
    btn_withdraw.textContent = "withdraw"
    const btn_deposit = document.createElement('button');
    btn_deposit.textContent = "deposit"

    root.appendChild(balance)
    root.appendChild(input_money)
    root.appendChild(btn_deposit)
    root.appendChild(btn_withdraw)

}
